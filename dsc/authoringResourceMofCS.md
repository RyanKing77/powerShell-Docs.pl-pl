---
ms.date: 06/12/2017
keywords: Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia
title: Tworzenie zasobu usługi Konfiguracja DSC w języku C#
ms.openlocfilehash: e8d3561f197950137877fc902063e43cbfc258ad
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222126"
---
# <a name="authoring-a-dsc-resource-in-c"></a>Tworzenie zasobu usługi Konfiguracja DSC w języku C#

> Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0

Zazwyczaj zasobów niestandardowych Windows PowerShell Desired stan konfiguracji (DSC) jest zaimplementowana w skrypt programu PowerShell. Można jednak zaimplementować funkcji DSC niestandardowego zasobu pisząc poleceń cmdlet w języku C#. Aby obejrzeć wprowadzenie o pisaniu poleceń cmdlet w języku C#, zobacz [zapisywania polecenie Cmdlet programu Windows PowerShell](https://technet.microsoft.com/library/dd878294.aspx).

Jako uzupełnienie implementacja zasobu w języku C# jako polecenia cmdlet, proces tworzenia schematu MOF, tworzenie struktury folderów, importowanie i przy użyciu niestandardowego zasobu DSC są takie same, zgodnie z opisem w [pisania niestandardowego zasobu DSC z MOF](authoringResourceMOF.md).

## <a name="writing-a-cmdlet-based-resource"></a>Zapisywanie oparte na poleceniach cmdlet zasobu
Na przykład wprowadzimy proste zasobu, który zarządza plik tekstowy i jego zawartość.

### <a name="writing-the-mof-schema"></a>Zapisywanie schematu MOF

Poniżej znajduje się definicja zasobu MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a>Konfigurowanie projektu programu Visual Studio
#### <a name="setting-up-a-cmdlet-project"></a>Konfigurowanie projektu polecenia cmdlet

1. Otwórz program Visual Studio.
1. Tworzenie projektu C# i podaj nazwę.
1. Wybierz **biblioteki klas** z szablonów projektu dostępne.
1. Kliknij przycisk **Ok**.
1. Dodaj odwołanie do zestawu do System.Automation.Management.dll do projektu.
1. Zmień nazwę zestawu, aby być zgodna z nazwą zasobu. W takim przypadku powinno być nazwanym zestawie **MSFT_XDemoFile**.

### <a name="writing-the-cmdlet-code"></a>Pisanie kodu polecenia cmdlet

Poniższy kod C# implementuje **Get-TargetResource**, **TargetResource zestaw**, i **TargetResource testu** poleceń cmdlet.

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a>Wdrażanie zasobu

Plik skompilowanej biblioteki dll powinien zostać zapisany w strukturze plików podobne do zasobów opartych na skryptach. Poniżej znajduje się struktura folderów dla tego zasobu.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a>Zobacz też
#### <a name="concepts"></a>Pojęcia
[Pisanie niestandardowych zasobów DSC z MOF](authoringResourceMOF.md)
#### <a name="other-resources"></a>Inne zasoby
[Pisanie polecenie Cmdlet programu Windows PowerShell](https://msdn.microsoft.com/library/dd878294.aspx)