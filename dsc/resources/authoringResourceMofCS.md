---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguracja, ustawienia
title: Tworzenie zasobu DSC wC#
ms.openlocfilehash: 6f2bb4d411237f13e2735c2e5f630b4f40dc6842
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794233"
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="24e60-103">Tworzenie zasobu DSC w języku C\#</span><span class="sxs-lookup"><span data-stu-id="24e60-103">Authoring a DSC resource in C\#</span></span>

> <span data-ttu-id="24e60-104">Dotyczy: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24e60-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="24e60-105">Zazwyczaj zasób niestandardowy Windows PowerShell Desired State Configuration (DSC) jest implementowany w skrypcie programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24e60-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="24e60-106">Jednak możesz również wdrożyć funkcje zasób niestandardowy DSC, pisząc poleceń cmdlet C#.</span><span class="sxs-lookup"><span data-stu-id="24e60-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="24e60-107">Aby zapoznać się na pisaniu poleceń cmdlet C#, zobacz [pisania polecenia Cmdlet programu Windows PowerShell](/powershell/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="24e60-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](/powershell/developer/windows-powershell).</span></span>

<span data-ttu-id="24e60-108">Oprócz wdrażania zasobów w C# jako polecenia cmdlet, proces trwa tworzenie schematu pliku MOF, tworzenia struktury folderów, importowania i używania niestandardowego zasobu DSC są takie same, zgodnie z opisem w [pisanie zasobu DSC niestandardowych z pliku MOF](authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="24e60-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="24e60-109">Pisanie zasobu opartą na poleceniach cmdlet</span><span class="sxs-lookup"><span data-stu-id="24e60-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="24e60-110">W tym przykładzie wdrożymy prosty zasób, który zarządza plik tekstowy i jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="24e60-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="24e60-111">Zapisywanie schematu pliku MOF</span><span class="sxs-lookup"><span data-stu-id="24e60-111">Writing the MOF schema</span></span>

<span data-ttu-id="24e60-112">Poniżej znajduje się plik MOF definicji zasobu.</span><span class="sxs-lookup"><span data-stu-id="24e60-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="24e60-113">Konfigurowanie projektu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="24e60-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="24e60-114">Konfigurowanie projektu polecenia cmdlet</span><span class="sxs-lookup"><span data-stu-id="24e60-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="24e60-115">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="24e60-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="24e60-116">Tworzenie C# projektu, a następnie podaj nazwę.</span><span class="sxs-lookup"><span data-stu-id="24e60-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="24e60-117">Wybierz **biblioteki klas** z dostępnych szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="24e60-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="24e60-118">Kliknij przycisk **Ok**.</span><span class="sxs-lookup"><span data-stu-id="24e60-118">Click **Ok**.</span></span>
1. <span data-ttu-id="24e60-119">Dodaj odwołanie do zestawu do System.Automation.Management.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="24e60-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="24e60-120">Zmień nazwę zestawu, aby dopasować nazwę zasobu.</span><span class="sxs-lookup"><span data-stu-id="24e60-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="24e60-121">W tym przypadku powinien zostać nazwany zestaw **MSFT_XDemoFile**.</span><span class="sxs-lookup"><span data-stu-id="24e60-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="24e60-122">Pisanie kodu polecenie cmdlet</span><span class="sxs-lookup"><span data-stu-id="24e60-122">Writing the cmdlet code</span></span>

<span data-ttu-id="24e60-123">Następujące C# kod implementuje **Get TargetResource**, **TargetResource zestaw**, i **TargetResource testu** polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24e60-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

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

### <a name="deploying-the-resource"></a><span data-ttu-id="24e60-124">Wdrażanie zasobu</span><span class="sxs-lookup"><span data-stu-id="24e60-124">Deploying the resource</span></span>

<span data-ttu-id="24e60-125">Plik skompilowanej biblioteki dll powinny być zapisywane w pliku struktury podobnej do zasobów opartych na skryptach.</span><span class="sxs-lookup"><span data-stu-id="24e60-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="24e60-126">Poniżej przedstawiono strukturę folderów dla tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="24e60-126">The following is the folder structure for this resource.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="24e60-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24e60-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="24e60-128">Pojęcia</span><span class="sxs-lookup"><span data-stu-id="24e60-128">Concepts</span></span>
[<span data-ttu-id="24e60-129">Pisanie zasobu DSC niestandardowych z pliku MOF</span><span class="sxs-lookup"><span data-stu-id="24e60-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="24e60-130">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="24e60-130">Other Resources</span></span>
[<span data-ttu-id="24e60-131">Zapisywanie polecenia Cmdlet programu Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24e60-131">Writing a Windows PowerShell Cmdlet</span></span>](/powershell/developer/windows-powershell)