---
title: Tworzenie polecenia cmdlet w celu uzyskania dostępu do magazynu danych
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 7acccbd48dcfb654b11e448a1f24835ad3668fae
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104465"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Tworzenie polecenia cmdlet w celu uzyskania dostępu do magazynu danych

W tej sekcji opisano sposób tworzenia polecenia cmdlet, które uzyskuje dostęp do przechowywanych danych za pomocą dostawcy środowiska Windows PowerShell. Ten typ polecenia cmdlet używa infrastruktury dostawcy programu Windows PowerShell środowiska uruchomieniowego programu Windows PowerShell i dlatego Klasa poleceń cmdlet musi pochodzić od klasy bazowej [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

Opisane w tym miejscu polecenie cmdlet Select-str może lokalizować i wybierać ciągi w pliku lub obiekcie. Wzorce używane do identyfikacji ciągu można jawnie określić za pomocą `Path` parametru polecenia cmdlet lub niejawnie `Script` za pomocą parametru.

Polecenie cmdlet jest przeznaczone do używania dowolnego dostawcy środowiska Windows PowerShell, który pochodzi od [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Na przykład polecenie cmdlet może określić dostawcę systemu plików lub dostawcę zmiennych, który jest dostarczany przez program Windows PowerShell. Aby uzyskać więcej informacji aboutWindows dostawców programu PowerShell, zobacz [projektowanie dostawcy środowiska Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).

## <a name="defining-the-cmdlet-class"></a>Definiowanie klasy poleceń cmdlet

Pierwszym krokiem w tworzeniu poleceń cmdlet jest zawsze nazywanie polecenia cmdlet i deklarowanie klasy .NET, która implementuje polecenie cmdlet. To polecenie cmdlet wykrywa pewne ciągi, więc nazwa zlecenia wybrana w tym miejscu to "Select" zdefiniowanego przez klasę [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) . Nazwa rzeczownika "str" jest używana, ponieważ polecenie cmdlet działa w przypadku ciągów. W deklaracji poniżej należy zauważyć, że czasownik poleceń cmdlet i nazwa rzeczownika są odzwierciedlone w nazwie klasy poleceń cmdlet. Aby uzyskać więcej informacji na temat zatwierdzonych zleceń poleceń cmdlet, zobacz [nazwy zleceń poleceń cmdlet](./approved-verbs-for-windows-powershell-commands.md).

Klasa .NET dla tego polecenia cmdlet musi być pochodną klasy bazowej [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , ponieważ zapewnia obsługę wymaganą przez środowisko uruchomieniowe środowiska Windows PowerShell, aby uwidocznić infrastrukturę dostawcy środowiska Windows PowerShell. Należy zauważyć, że to polecenie cmdlet korzysta również z klas wyrażeń regularnych .NET Framework, takich jak [System. Text. RegularExpressions. wyrażenia](/dotnet/api/System.Text.RegularExpressions.Regex)regularnego.

Poniższy kod jest definicją klasy dla tego polecenia cmdlet Select-str.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

To polecenie cmdlet definiuje domyślny parametr ustawiony przez dodanie `DefaultParameterSetName` słowa kluczowego Attribute do deklaracji klasy. Domyślny zestaw `PatternParameterSet` parametrów jest używany, `Script` gdy parametr nie jest określony. Aby uzyskać więcej informacji na temat tego zestawu parametrów, `Pattern` zobacz `Script` Omówienie parametrów i w poniższej sekcji.

## <a name="defining-parameters-for-data-access"></a>Definiowanie parametrów dostępu do danych

To polecenie cmdlet definiuje kilka parametrów, które umożliwiają użytkownikowi dostęp do danych przechowywanych i sprawdzanie ich. Parametry te zawierają `Path` parametr wskazujący lokalizację magazynu danych `Pattern` , parametr określający wzorzec, który ma być używany w wyszukiwaniu, a także kilka innych parametrów, które obsługują sposób wyszukiwania.

> [!NOTE]
> Aby uzyskać więcej informacji na temat podstawy definiowania parametrów, zobacz [Dodawanie parametrów, które przetwarzają dane wejściowe wiersza polecenia](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Deklarowanie parametru Path

Aby zlokalizować magazyn danych, to polecenie cmdlet musi używać ścieżki programu Windows PowerShell do identyfikowania dostawcy środowiska Windows PowerShell, który jest przeznaczony do uzyskiwania dostępu do magazynu danych. W związku z tym definiuje `Path` parametr typu String array, aby wskazać lokalizację dostawcy.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Należy zauważyć, że ten parametr należy do dwóch różnych zestawów parametrów i ma alias.

Dwa atrybuty [System. Management. Automation. ParameterAttribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklarują, `Path` że `ScriptParameterSet` parametr należy `PatternParameterSet`do i. Aby uzyskać więcej informacji na temat zestawów parametrów, zobacz [Dodawanie zestawów parametrów do polecenia cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

Atrybut [System. Management. Automation. aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) deklaruje `PSPath` alias dla `Path` parametru. Deklarowanie tego aliasu jest zdecydowanie zalecane w przypadku spójności z innymi poleceniami cmdlet, które uzyskują dostęp do dostawców programu Windows PowerShell. Aby uzyskać więcej informacji aboutWindows ścieżki programu PowerShell, zobacz "koncepcje ścieżek programu PowerShell" w temacie [jak działa środowisko Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="declaring-the-pattern-parameter"></a>Deklarowanie parametru wzorca

Aby określić wzorce do wyszukania, to polecenie cmdlet deklaruje `Pattern` parametr, który jest tablicą ciągów. Wynik pozytywny jest zwracany, jeśli którykolwiek z wzorców zostanie znaleziony w magazynie danych. Należy zauważyć, że wzorce te można kompilować do tablicy skompilowanych wyrażeń regularnych lub tablicy symboli wieloznacznych używanych do wyszukiwania literałów.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Jeśli ten parametr jest określony, polecenie cmdlet używa domyślnego zestawu `PatternParameterSet`parametrów. W takim przypadku polecenie cmdlet używa wzorców określonych w tym miejscu, aby wybrać ciągi. Z kolei `Script` można także użyć parametru, aby dostarczyć skrypt, który zawiera wzorce. Parametry `Script` i`Pattern` definiują dwa oddzielne zestawy parametrów, aby wykluczają się wzajemnie.

### <a name="declaring-search-support-parameters"></a>Deklarowanie parametrów obsługi wyszukiwania

To polecenie cmdlet definiuje następujące parametry obsługi, których można użyć w celu zmodyfikowania możliwości wyszukiwania w poleceniu cmdlet.

`Script` Parametr określa blok skryptu, którego można użyć, aby zapewnić alternatywny mechanizm wyszukiwania dla polecenia cmdlet. Skrypt musi zawierać wzorce używane do dopasowywania i zwracania obiektu [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) . Należy zauważyć, że ten parametr jest również unikatowym parametrem `ScriptParameterSet` , który identyfikuje zestaw parametrów. Gdy środowisko uruchomieniowe programu Windows PowerShell widzi ten parametr, używa tylko parametrów, które należą `ScriptParameterSet` do zestawu parametrów.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

`SimpleMatch` Parametr jest parametrem Switch, który wskazuje, czy polecenie cmdlet jest jawnie zgodne ze wzorcami w miarę ich dostarczania. Gdy użytkownik określi parametr w wierszu polecenia (`true`), polecenie cmdlet używa wzorców w miarę ich dostarczania. Jeśli parametr nie jest określony (`false`), polecenie cmdlet używa wyrażeń regularnych. Wartość domyślna tego parametru to `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

`CaseSensitive` Parametr jest parametrem Switch, który wskazuje, czy jest wykonywane wyszukiwanie z uwzględnieniem wielkości liter. Gdy użytkownik określi parametr w wierszu polecenia (`true`), polecenie cmdlet sprawdza wielkie i małe litery znaków podczas porównywania wzorców. Jeśli parametr nie jest określony (`false`), polecenie cmdlet nie rozróżnia wielkich i małych liter. Na przykład "Moje pliki" i "Moje pliki" byłyby zwracane jako dodatnie trafienia. Wartość domyślna tego parametru to `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

Parametry `Exclude` i`Include` identyfikują elementy, które są jawnie wyłączone lub uwzględnione w wyszukiwaniu. Domyślnie polecenie cmdlet przeszuka wszystkie elementy w magazynie danych. Aby jednak ograniczyć wyszukiwanie wykonywane przez polecenie cmdlet, można jawnie wskazać elementy, które mają być uwzględnione w wyszukiwaniu lub pominięte.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>Deklarowanie zestawów parametrów

To polecenie cmdlet używa dwóch zestawów parametrów`ScriptParameterSet` ( `PatternParameterSet`i, co jest ustawieniem domyślnym) jako nazw dwóch zestawów parametrów używanych w dostępie do danych. `PatternParameterSet`jest domyślnym zestawem parametrów i jest używany, gdy `Pattern` parametr jest określony. `ScriptParameterSet`jest używany, gdy użytkownik określa alternatywny mechanizm wyszukiwania za pomocą `Script` parametru. Aby uzyskać więcej informacji na temat zestawów parametrów, zobacz [Dodawanie zestawów parametrów do polecenia cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Zastępowanie metod przetwarzania wejściowego

Polecenia cmdlet muszą przesłaniać co najmniej jedną metodę przetwarzania danych wejściowych dla klasy [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Aby uzyskać więcej informacji na temat metod przetwarzania danych wejściowych, zobacz [Tworzenie pierwszego polecenia cmdlet](./creating-a-cmdlet-without-parameters.md).

To polecenie cmdlet zastępuje metodę [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , aby kompilować tablicę skompilowanych wyrażeń regularnych przy uruchamianiu. Zwiększa to wydajność podczas wyszukiwania, które nie używają prostego dopasowywania.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

To polecenie cmdlet przesłania również metodę [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , aby przetworzyć wybrane przez użytkownika w wierszu polecenia. Zapisuje wyniki wyboru ciągu w formie niestandardowego obiektu przez wywołanie prywatnej metody **MatchString** .

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>Uzyskiwanie dostępu do zawartości

Polecenie cmdlet musi otworzyć dostawcę wskazanego przez ścieżkę programu Windows PowerShell, aby mógł on uzyskać dostęp do danych. Obiekt [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) dla obszaru działania jest używany na potrzeby dostępu do dostawcy, podczas gdy do otwierania dostawcy jest używane Właściwość [System. Management. Automation. PSCmdlet. Invokeprovider *](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) polecenia cmdlet. Dostęp do zawartości jest zapewniany przez pobranie obiektu [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) dla otwartego dostawcy.

To przykładowe polecenie cmdlet Select-str używa właściwości [System. Management. Automation. Providerintrinsics. Content *](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) , aby udostępnić zawartość do skanowania. Następnie może wywołać metodę [System. Management. Automation. Contentcmdletproviderintrinsics. GetReader *](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) , przekazując wymaganą ścieżkę środowiska Windows PowerShell.

## <a name="code-sample"></a>Przykładowy kod

Poniższy kod przedstawia implementację tej wersji tego polecenia cmdlet Select-str. Należy zauważyć, że ten kod zawiera klasę poleceń cmdlet, metody prywatne używane przez polecenie cmdlet i kod przystawki programu Windows PowerShell służący do rejestrowania tego polecenia cmdlet. Aby uzyskać więcej informacji na temat rejestrowania polecenia cmdlet, zobacz [Tworzenie polecenia cmdlet](#defining-the-cmdlet-class).

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>Kompilowanie polecenia cmdlet

Po wdrożeniu polecenia cmdlet należy zarejestrować go za pomocą programu Windows PowerShell za pomocą przystawki programu Windows PowerShell. Aby uzyskać więcej informacji na temat rejestrowania poleceń cmdlet, zobacz [jak zarejestrować polecenia cmdlet, dostawców i aplikacje hosta](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testowanie polecenia cmdlet

Gdy polecenie cmdlet zostało zarejestrowane w programie Windows PowerShell, można je przetestować, uruchamiając je w wierszu polecenia. Poniższa procedura służy do testowania przykładowego polecenia cmdlet Select-str.

1. Uruchom program Windows PowerShell i Wyszukaj w pliku uwagi wystąpienia wierszy z wyrażeniem ".NET". Należy zauważyć, że znaki cudzysłowu wokół nazwy ścieżki są wymagane tylko wtedy, gdy ścieżka składa się z więcej niż jednego wyrazu.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    Pojawią się następujące dane wyjściowe.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Wyszukaj w pliku notatek wystąpienia wierszy z słowem "Over", po którym następuje inny tekst. `SimpleMatch` Parametr używa wartości domyślnej `false`. W wyszukiwaniu nie jest rozróżniana wielkość `CaseSensitive` liter, ponieważ parametr `false`jest ustawiony na.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    Pojawią się następujące dane wyjściowe.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. Przeszukaj plik uwag przy użyciu wyrażenia regularnego jako wzorca. Polecenie cmdlet wyszukuje znaki alfabetyczne i puste spacje ujęte w nawiasy.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    Pojawią się następujące dane wyjściowe.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. Wykonaj wyszukiwanie w pliku uwag z uwzględnieniem wielkości liter dla wystąpień słowa "parameter".

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    Pojawią się następujące dane wyjściowe.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. Przeszukaj dostawcę zmiennej dostarczonego z programem Windows PowerShell dla zmiennych, które mają wartości liczbowe z przestawu od 0 do 9.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    Pojawią się następujące dane wyjściowe.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Użyj bloku skryptu, aby przeszukać plik SelectStrCommandSample.cs dla ciągu "pos". Funkcja **cmatch —** dla skryptu wykonuje dopasowanie do wzorca bez uwzględniania wielkości liter.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    Pojawią się następujące dane wyjściowe.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Zobacz też

[Jak utworzyć polecenie cmdlet programu Windows PowerShell](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Tworzenie pierwszego polecenia cmdlet](./creating-a-cmdlet-without-parameters.md)

[Tworzenie polecenia cmdlet modyfikującego system](./creating-a-cmdlet-that-modifies-the-system.md)

[Projektowanie dostawcy środowiska Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md)

[Jak działa środowisko Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Jak zarejestrować polecenia cmdlet, dostawców i aplikacje hosta](/previous-versions//ms714644(v=vs.85))

[Zestaw SDK programu Windows PowerShell](../windows-powershell-reference.md)
