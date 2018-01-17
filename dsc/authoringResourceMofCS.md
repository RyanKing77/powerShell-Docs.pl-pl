---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "Konfiguracja DSC środowiska powershell, konfiguracji, ustawienia"
title: "Tworzenie zasobu usługi Konfiguracja DSC w języku C#"
ms.openlocfilehash: 2fc6b8c127bca29e8f66fc7bd8d2828fdfe39f3c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="5131d-103">Tworzenie zasobu usługi Konfiguracja DSC w języku C#</span><span class="sxs-lookup"><span data-stu-id="5131d-103">Authoring a DSC resource in C#</span></span>

> <span data-ttu-id="5131d-104">Dotyczy: Środowiska Windows PowerShell 4.0, programu Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5131d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5131d-105">Zazwyczaj zasobów niestandardowych Windows PowerShell Desired stan konfiguracji (DSC) jest zaimplementowana w skrypt programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5131d-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="5131d-106">Można jednak zaimplementować funkcji DSC niestandardowego zasobu pisząc poleceń cmdlet w języku C#.</span><span class="sxs-lookup"><span data-stu-id="5131d-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="5131d-107">Aby obejrzeć wprowadzenie o pisaniu poleceń cmdlet w języku C#, zobacz [zapisywania polecenie Cmdlet programu Windows PowerShell](https://technet.microsoft.com/en-us/library/dd878294.aspx).</span><span class="sxs-lookup"><span data-stu-id="5131d-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx).</span></span>

<span data-ttu-id="5131d-108">Jako uzupełnienie implementacja zasobu w języku C# jako polecenia cmdlet, proces tworzenia schematu MOF, tworzenie struktury folderów, importowanie i przy użyciu niestandardowego zasobu DSC są takie same, zgodnie z opisem w [pisania niestandardowego zasobu DSC z MOF](authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="5131d-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="5131d-109">Zapisywanie oparte na poleceniach cmdlet zasobu</span><span class="sxs-lookup"><span data-stu-id="5131d-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="5131d-110">Na przykład wprowadzimy proste zasobu, który zarządza plik tekstowy i jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="5131d-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="5131d-111">Zapisywanie schematu MOF</span><span class="sxs-lookup"><span data-stu-id="5131d-111">Writing the MOF schema</span></span>

<span data-ttu-id="5131d-112">Poniżej znajduje się definicja zasobu MOF.</span><span class="sxs-lookup"><span data-stu-id="5131d-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="5131d-113">Konfigurowanie projektu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5131d-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="5131d-114">Konfigurowanie projektu polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="5131d-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="5131d-115">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5131d-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="5131d-116">Tworzenie projektu C# i podaj nazwę.</span><span class="sxs-lookup"><span data-stu-id="5131d-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="5131d-117">Wybierz **biblioteki klas** z szablonów projektu dostępne.</span><span class="sxs-lookup"><span data-stu-id="5131d-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="5131d-118">Kliknij przycisk **Ok**.</span><span class="sxs-lookup"><span data-stu-id="5131d-118">Click **Ok**.</span></span>
1. <span data-ttu-id="5131d-119">Dodaj odwołanie do zestawu do System.Automation.Management.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="5131d-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="5131d-120">Zmień nazwę zestawu, aby być zgodna z nazwą zasobu.</span><span class="sxs-lookup"><span data-stu-id="5131d-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="5131d-121">W takim przypadku powinno być nazwanym zestawie **MSFT_XDemoFile**.</span><span class="sxs-lookup"><span data-stu-id="5131d-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="5131d-122">Pisanie kodu polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="5131d-122">Writing the cmdlet code</span></span>

<span data-ttu-id="5131d-123">Poniższy kod C# implementuje **Get-TargetResource**, **TargetResource zestaw**, i **TargetResource testu** poleceń cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5131d-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

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

### <a name="deploying-the-resource"></a><span data-ttu-id="5131d-124">Wdrażanie zasobu</span><span class="sxs-lookup"><span data-stu-id="5131d-124">Deploying the resource</span></span>

<span data-ttu-id="5131d-125">Plik skompilowanej biblioteki dll powinien zostać zapisany w strukturze plików podobne do zasobów opartych na skryptach.</span><span class="sxs-lookup"><span data-stu-id="5131d-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="5131d-126">Poniżej znajduje się struktura folderów dla tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="5131d-126">The following is the folder structure for this resource.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="5131d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5131d-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="5131d-128">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="5131d-128">Concepts</span></span>
[<span data-ttu-id="5131d-129">Pisanie niestandardowych zasobów DSC z MOF</span><span class="sxs-lookup"><span data-stu-id="5131d-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="5131d-130">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="5131d-130">Other Resources</span></span>
[<span data-ttu-id="5131d-131">Pisanie polecenie Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5131d-131">Writing a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/library/dd878294.aspx)

