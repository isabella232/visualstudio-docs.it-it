---
title: Personalizzazione dell'analisi code coverage
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8749cd7757796a1b716b1ac9db086d3155f94694
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965551"
---
# <a name="customize-code-coverage-analysis"></a>Personalizzare l'analisi code coverage

Per impostazione predefinita, il code coverage analizza tutti gli assembly della soluzione caricati durante gli unit test. È consigliabile usare questo comportamento predefinito poiché funziona bene nella maggior parte dei casi. Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Per escludere il codice di test dai risultati del code coverage e includere solo il codice dell'applicazione, aggiungere l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> alla classe di test.

Per includere assembly che non fanno parte della soluzione, ottenere i file *PDB* per tali assembly e copiarli nella stessa cartella dei file *DLL* dell'assembly.

## <a name="run-settings-file"></a>File di impostazioni esecuzione test

Il [file di impostazioni esecuzione test](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) è il file di configurazione usato dagli strumenti di testing unità. Le impostazioni avanzate di code coverage vengono specificate in un file con estensione *runsettings*.

Per personalizzare il code coverage, seguire questa procedura:

1. Aggiungere un file di impostazioni esecuzione test alla propria soluzione. In **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo elemento** dal menu di scelta rapida della soluzione e selezionare **File XML**. Salvare il file con un nome come *CodeCoverage.runsettings*.

1. Aggiungere il contenuto riportato nel file di esempio alla fine di questo articolo, quindi personalizzarlo secondo le proprie esigenze come descritto nelle sezioni seguenti.

1. Per selezionare il file di impostazioni esecuzione test, nel menu **Test** scegliere **Impostazioni test** > **Seleziona file di impostazioni test**. Per specificare un file di impostazioni esecuzione test per l'esecuzione di test dalla riga di comando o in un flusso di lavoro di compilazione, vedere [Configurare unit test usando un file *con estensione runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Quando si seleziona **Analizza code coverage** le informazioni di configurazione vengono lette dal file di impostazioni esecuzione test.

   > [!TIP]
   > I risultati del code coverage precedente e la colorazione del codice non vengono nascosti automaticamente quando si eseguono i test o si aggiorna il codice.

Per attivare e disattivare le impostazioni personalizzate, deselezionare o selezionare il file nel menu **Test** > **Impostazioni test**.

![Menu Impostazioni test con file di impostazioni personalizzato](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Specificare i percorsi di ricerca dei simboli

Il code coverage richiede file di simboli (file *PDB*) per gli assembly. Per gli assembly compilati dalla soluzione, i file di simboli sono solitamente presenti accanto ai file binari e il code coverage viene eseguito automaticamente. In alcuni casi invece è consigliabile includere assembly a cui si fa riferimento nell'analisi del code coverage. In questi casi i file *PDB* non possono essere adiacenti ai binari, ma è possibile specificare il percorso di ricerca dei simboli nel file *RUNSETTINGS*.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> La risoluzione dei simboli può richiedere tempo, in particolare quando si usa un percorso file remoto con molti assembly. Di conseguenza, si consiglia di copiare i file *PDB* nello stesso percorso locale dei file binari (*DLL* ed *EXE*).

### <a name="exclude-and-include"></a>Exclude e include

È possibile escludere gli assembly specificati dall'analisi code coverage. Ad esempio:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

In alternativa, è possibile specificare gli assembly che devono essere inclusi. Questo approccio presenta lo svantaggio che quando si aggiungono più assembly alla soluzione, è necessario tenere a mente che occorre aggiungerli anche all'elenco:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Se l'elemento **Include** è vuoto, l'elaborazione del code coverage include tutti gli assembly caricati e per cui è possibile trovare file *PDB*. Il code coverage non include gli elementi che corrispondono a una clausola in un elenco **Exclude**.

**Include** viene elaborato prima di **Exclude**.

### <a name="regular-expressions"></a>Espressioni regolari

Includere ed escludere i nodi che usano le espressioni regolari. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Le espressioni regolari non equivalgono ai caratteri jolly. In particolare:

- **.\\** * corrisponde a una stringa composta da caratteri qualsiasi

- **\\.** corrisponde a un punto "."

- **\\(   \\)** corrisponde alle parentesi "(  )"

- **\\\\** corrisponde al delimitatore del percorso di file "\\"

- **^** corrisponde all'inizio della stringa

- **$** corrisponde alla fine della stringa

Tutte le corrispondenze fanno distinzione tra maiuscole e minuscole.

Ad esempio:

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

> [!WARNING]
> Se è presente un errore in un'espressione regolare, ad esempio un carattere senza codice di escape o parentesi non corrispondenti, l'analisi di code coverage non funzionerà.

### <a name="other-ways-to-include-or-exclude-elements"></a>Altri modi per includere o escludere elementi

- **ModulePath**: corrisponde agli assembly specificati in base al percorso del file di assembly.

- **CompanyName**: corrisponde agli assembly in base all'attributo **Company**.

- **PublicKeyToken**: corrisponde agli assembly firmati in base al token di chiave pubblica.

- **Source**: corrisponde agli elementi in base al nome del percorso del file di origine in cui sono definiti.

- **Attribute**: corrisponde agli elementi ai quali è allegato un particolare attributo. Specificare il nome completo dell'attributo e includere "Attribute" alla fine del nome.

- **Function**: corrisponde a procedure, funzioni o metodi in base al nome completo. Per corrispondere a un nome di funzione, l'espressione regolare deve corrispondere al nome completo della funzione, inclusi spazio dei nomi, nome della classe, nome del metodo ed elenco di parametri. Ad esempio:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

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
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
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
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
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
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Vedere anche

- [Configurare unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Eseguire unit test del codice](../test/unit-test-your-code.md)