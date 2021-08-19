---
title: Personalizzazione dell'analisi code coverage
description: Informazioni su come usare l'attributo ExcludeFromCodeCoverageAttribute per escludere il codice di test dai risultati di code coverage. È possibile includere assembly all'esterno della soluzione.
ms.custom: SEO-VS-2020
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b422efc8e3f8e6ec9c39b02089e22c5eab6ed3cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083934"
---
# <a name="customize-code-coverage-analysis"></a>Personalizzare l'analisi code coverage

Per impostazione predefinita, il code coverage analizza tutti gli assembly della soluzione caricati durante gli unit test. È consigliabile usare questo comportamento predefinito poiché funziona bene nella maggior parte dei casi. Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Per escludere il codice di test dai risultati del code coverage e includere solo il codice dell'applicazione, aggiungere l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> alla classe di test.

Per includere assembly che non fanno parte della soluzione, ottenere i file *PDB* per tali assembly e copiarli nella stessa cartella dei file *DLL* dell'assembly.

## <a name="run-settings-file"></a>File di impostazioni esecuzione test

Il [file delle impostazioni di esecuzione](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) è il file di configurazione usato dagli strumenti di unit test. Le code coverage avanzate vengono specificate in un file *con estensione runsettings.*

Per personalizzare il code coverage, seguire questa procedura:

1. Aggiungere un file di impostazioni esecuzione test alla propria soluzione. In **Esplora soluzioni** scegliere Aggiungi nuovo elemento dal menu di scelta rapida della soluzione  >  e selezionare File **XML**. Salvare il file con un nome come *CodeCoverage.runsettings*.

2. Aggiungere il contenuto riportato nel file di esempio alla fine di questo articolo, quindi personalizzarlo secondo le proprie esigenze come descritto nelle sezioni seguenti.

::: moniker range="vs-2017"

3. Per selezionare il file di impostazioni esecuzione test, nel menu **Test** scegliere **Impostazioni test** > **Seleziona file di impostazioni test**. Per specificare un file di impostazioni esecuzione test per l'esecuzione di test dalla riga di comando, vedere [Configurare unit test](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Per selezionare il file delle impostazioni di esecuzione, **scegliere** Seleziona Impostazioni file dal menu **Test**. Per specificare un file di impostazioni esecuzione test per l'esecuzione di test dalla riga di comando, vedere [Configurare unit test](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

   Quando si seleziona **Analizza code coverage** le informazioni di configurazione vengono lette dal file di impostazioni esecuzione test.

   > [!TIP]
   > Gli eventuali risultati del code coverage precedente e la colorazione del codice non vengono nascosti automaticamente quando si eseguono i test o si aggiorna il codice.

::: moniker range="vs-2017"

Per disattivare e attivare le impostazioni personalizzate,  deselezionare o selezionare il file nel menu > **Test Impostazioni** test.

![Menu Impostazioni test con file di impostazioni personalizzato in Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Per disattivare e attivare le impostazioni personalizzate, deselezionare o selezionare il file nel menu **Test.**

::: moniker-end

## <a name="symbol-search-paths"></a>Percorsi di ricerca dei simboli

Il code coverage richiede file di simboli (file *PDB*) per gli assembly. Per gli assembly compilati dalla soluzione, i file di simboli sono solitamente presenti accanto ai file binari e il code coverage viene eseguito automaticamente. In alcuni casi è consigliabile includere gli assembly a cui si fa riferimento nell'analisi del code coverage. In questi casi, i *file con estensione pdb* potrebbero non essere adiacenti ai file binari, ma è possibile specificare il percorso di ricerca dei simboli nel file con estensione *runsettings.*

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> La risoluzione dei simboli può richiedere tempo, in particolare quando si usa un percorso file remoto con molti assembly. Di conseguenza, si consiglia di copiare i file *PDB* nello stesso percorso locale dei file binari (*DLL* ed *EXE*).

## <a name="include-or-exclude-assemblies-and-members"></a>Includere o escludere assembly e membri

È possibile includere o escludere assembly o tipi e membri specifici dall code coverage a analisi. Se la **sezione Include** è vuota o omessa, vengono inclusi tutti gli assembly caricati e a cui sono associati file PDB. Se un assembly o un membro corrisponde a una clausola nella **sezione Exclude,** viene escluso dal code coverage. La **sezione Exclude** ha la precedenza sulla sezione **Include:** se un assembly è elencato in **Include** ed **Exclude,** non verrà incluso in code coverage.

Ad esempio, il codice XML seguente esclude un singolo assembly specificandone il nome:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

L'esempio seguente specifica che deve essere incluso un solo assembly in code coverage:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

La tabella seguente illustra i diversi modi in cui è possibile trovare la corrispondenza tra assembly e membri per l'inclusione o l'esclusione da code coverage.

| Elemento XML | Elementi corrispondenti |
| - | - |
| ModulePath | Corrisponde agli assembly specificati dal nome dell'assembly o dal percorso del file. |
| CompanyName | Corrisponde agli assembly in base **all'attributo** Company. |
| PublicKeyToken | Corrisponde agli assembly firmati dal token di chiave pubblica. |
| Source (Sorgente) | Trova la corrispondenza degli elementi in base al nome del percorso del file di origine in cui sono definiti. |
| Attributo | Trova la corrispondenza con gli elementi con l'attributo specificato. Specificare il nome completo dell'attributo, ad esempio `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`.<br/><br/>Se si esclude l'attributo <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute>, il codice che usa funzionalità del linguaggio come `async`, `await`, `yield return` e le proprietà implementate automaticamente viene escluso dall'analisi code coverage. Per escludere il codice effettivamente generato, escludere solo l'attributo <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. |
| Funzione | Corrisponde a procedure, funzioni o metodi in base al nome completo, incluso l'elenco di parametri. È anche possibile trovare una corrispondenza con parte del nome usando [un'espressione regolare](#regular-expressions).<br/><br/>Esempi:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` (C++) |

### <a name="regular-expressions"></a>Espressioni regolari

I nodi Includi ed Escludi usano espressioni regolari, che non sono uguali ai caratteri jolly. Tutte le corrispondenze fanno distinzione tra maiuscole e minuscole. Di seguito sono riportati alcuni esempi:

- **.\*** corrisponde a una stringa di qualsiasi carattere

- **\\.** corrisponde a un punto "."

- **\\ ( \\ )** corrisponde alle parentesi "( )"

- **\\\\** corrisponde a un delimitatore di percorso di file " \\ "

- **^** corrisponde all'inizio della stringa

- **$** corrisponde alla fine della stringa

Il codice XML seguente illustra come includere ed escludere assembly specifici usando espressioni regolari:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

Il codice XML seguente illustra come includere ed escludere funzioni specifiche usando espressioni regolari:

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

> [!WARNING]
> Se è presente un errore in un'espressione regolare, ad esempio un carattere senza codice di escape o parentesi non corrispondenti, l'analisi di code coverage non funzionerà.

Per altre informazioni sulle espressioni regolari, vedere [Usare espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>File con estensione runsettings di esempio

Copiare questo codice e modificarlo in base alle esigenze.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Vedi anche

- [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
