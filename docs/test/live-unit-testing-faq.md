---
title: Domande frequenti su Live Unit Testing
description: Esaminare queste Live Unit Testing domande frequenti, tra cui framework supportati, configurazione e personalizzazione.
ms.custom: SEO-VS-2020
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: bb2c9a4cae25b388d5817b04ff54f6e6443b2f44
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800507"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Domande frequenti su Live Unit Testing

## <a name="supported-frameworks"></a>Framework supportati

**Quali framework di test sono supportati da Live Unit Testing e quali sono le versioni minime supportate?**

Live Unit Testing è compatibile con i tre framework di testing unità elencati nella tabella riportata in seguito. Nella tabella è indicata anche la versione minima supportata degli adattatori e dei framework. I framework di unit test sono tutti disponibili su NuGet.org.

|Framework di test  |Versione minima dell'adattatore di Visual Studio  |Versione minima del framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versione 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versione 3.7.0 |NUnit versione 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se si hanno progetti di test basati su MSTest meno recenti che fanno riferimento e non si vuole passare ai pacchetti NuGet MSTest più recenti, eseguire `Microsoft.VisualStudio.QualityTools.UnitTestFramework` l'aggiornamento a Visual Studio 2019 o Visual Studio 2017.

In alcuni casi, per consentire il funzionamento di Live Unit Testing, potrebbe essere necessario ripristinare in modo esplicito i pacchetti NuGet a cui viene fatto riferimento nei progetti della soluzione. È possibile ripristinare i pacchetti eseguendo una compilazione esplicita della soluzione (selezionare Compila ricompila soluzione dal menu Visual Studio di primo livello) oppure facendo clic con il pulsante destro del mouse sulla soluzione e scegliendo Ripristina pacchetti NuGet prima di abilitare  >   Living Unit Testing. 

## <a name="net-core-support"></a>Supporto di .NET Core

**Live Unit Testing è compatibile con .NET Core?**

Sì. Live Unit Testing funziona con .NET Core e .NET Framework.

## <a name="configuration"></a>Configurazione

**Perché Live Unit Testing non funziona quando viene attivato?**

Quando è selezionato il menu a discesa Live Unit Testing, la finestra Output indica in genere il motivo per cui Live Unit Testing non funziona. È possibile che Live Unit Testing non funzioni per uno dei motivi seguenti:

- Se i pacchetti NuGet usati come riferimento nei progetti della soluzione non sono stati ripristinati, Live Unit Testing non funzionerà. Per risolvere il problema, eseguire una compilazione esplicita della soluzione o il ripristino dei pacchetti NuGet della soluzione prima di attivare Live Unit Testing.

- Se nei progetti si usano test basati su MSTest, verificare di rimuovere il riferimento a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e aggiungere i riferimenti alle versioni più recenti dei pacchetti NuGet di MSTest, ovvero `MSTest.TestAdapter` (è richiesta almeno la versione 1.1.11) e `MSTest.TestFramework` (è richiesta almeno la versione 1.1.11). Per altre informazioni, vedere la sezione "Framework di test supportati" nell'articolo [Usare Live Unit Testing in Visual Studio](live-unit-testing.md#supported-test-frameworks).

- Almeno un progetto della soluzione deve includere un riferimento a NuGet o un riferimento diretto al framework di test xUnit, NUnit o MSTest. Questo progetto deve anche fare riferimento a un pacchetto NuGet corrispondente degli adattatori di test di Visual Studio. È anche possibile usare un file con estensione *runsettings* per fare riferimento all'adattatore di test di Visual Studio. Il file con estensione *runsettings* deve contenere una voce simile a quella dell'esempio seguente:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Coverage errata dopo l'aggiornamento

**Perché Live Unit Testing mostra una coverage errata dopo aver aggiornato l'adattatore di test cui viene fatto riferimento nei progetti Visual Studio alla versione supportata?**

- Se più progetti nella soluzione fanno riferimento al pacchetto dell'adattatore di test NuGet, è necessario aggiornare ogni progetto alla versione supportata.

- Assicurarsi che anche il file *con estensione props* di MSBuild importato dal pacchetto dell'adattatore di test sia aggiornato correttamente. Controllare la versione o il percorso del pacchetto NuGet importato indicato in genere nella parte superiore del file di progetto, come illustrato di seguito:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Personalizzare le compilazioni

**È possibile personalizzare le compilazioni di Live Unit Testing?**

Se la soluzione richiede passaggi personalizzati per la compilazione per la strumentazione (Live Unit Testing) che non sono necessari per la compilazione "normale" non instrumentata, è possibile aggiungere codice al progetto o ai file con estensione *targets* che controlla la proprietà ed esegue passaggi `BuildingForLiveUnitTesting` di pre/post-compilazione personalizzati. È anche possibile scegliere di rimuovere alcune istruzioni di compilazione, ad esempio per la pubblicazione o la creazione di pacchetti, o di aggiungere istruzioni di compilazione, ad esempio per la copia dei prerequisiti, a una compilazione di Live Unit Testing in base a questa proprietà del progetto. La personalizzazione della compilazione basata su questa proprietà non altera in alcun modo la compilazione normale e influisce solo sulle compilazioni di Live Unit Testing.

Ad esempio, potrebbe essere presente una destinazione che produce pacchetti NuGet durante una compilazione normale. È probabile che non si vogliano generare pacchetti NuGet dopo ogni modifica apportata. È quindi possibile disabilitare tale destinazione nella compilazione di Live Unit Testing eseguendo quanto segue:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Messaggi di errore con \<OutputPath> , \<OutDir> o \<IntermediateOutputPath>

**Perché viene visualizzato l'errore seguente quando Live Unit Testing tenta di compilare la soluzione: "... sembra impostare in modo `<OutputPath>` incondizionato o `<OutDir>` . Live Unit Testing non eseguirà test dall'assembly di output"?**

È possibile ottenere questo errore se il processo di compilazione per la soluzione ha una logica personalizzata che specifica dove devono essere generati i file binari. Per impostazione predefinita, il percorso dei file binari dipende `<OutputPath>` da o , nonché da o `<OutDir>` `<IntermediateOutputPath>` `<BaseOutputPath>` `<BaseIntermediateOutputPath>` .

Live Unit Testing esegue l'override di tali variabili per assicurarsi che gli elementi di compilazione siano eliminati in una cartella di artefatti Live Unit Testing e avrà esito negativo se anche il processo di compilazione esegue l'override di queste variabili.

Esistono due approcci principali per creare Live Unit Testing compilazione corretta. Per configurazioni di compilazione più semplici, è possibile basare i percorsi di output su `<BaseIntermediateOutputPath>` . Per configurazioni più complesse è possibile basare i percorsi di output su `<LiveUnitTestingBuildRootPath>` .

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Override condizionale `<OutputPath>` / `<IntermediateOutputPath>` in base a `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` .

> [!NOTE]
> Per usare questo approccio, ogni progetto deve essere in grado di compilare in modo indipendente l'uno dall'altro. Non avere un elemento di riferimento del progetto da un altro progetto durante la compilazione. Non avere un progetto che carica in modo dinamico gli assembly da un altro progetto in fase di esecuzione (ad esempio, chiamare `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")` ).

Durante la compilazione, Live Unit Testing esegue automaticamente l'override delle variabili per `<BaseOutputPath>` / `<BaseIntermediateOutputPath>` la Live Unit Testing degli artefatti.

Se ad esempio la compilazione esegue l'override di <OutputPath> come illustrato di seguito:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

è possibile sostituirla con il codice XML seguente:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

In tal modo verrà garantita la presenza di `<OutputPath>` nella cartella `<BaseOutputPath>`.

Non eseguire l'override di `<OutDir>` direttamente nel processo di compilazione, ma eseguire l'override `<OutputPath>` per rilasciare gli artefatti di compilazione in un percorso specifico.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Override delle proprietà in base alla `<LiveUnitTestingBuildRootPath>` proprietà .

> [!NOTE]
> In questo approccio è necessario prestare attenzione ai file aggiunti nella cartella artifacts che non vengono generati durante la compilazione. L'esempio seguente illustra cosa fare quando si inserisce la cartella packages in artifacts. Poiché il contenuto di questa cartella non viene generato durante la compilazione, la proprietà MSBuild **non deve essere modificata.**

Durante una Live Unit Testing, la proprietà viene impostata sul percorso della `<LiveUnitTestingBuildRootPath>` Live Unit Testing artifacts.

Si supponga, ad esempio, che il progetto abbia la struttura illustrata di seguito.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Durante la Live Unit Testing compilazione, `<LiveUnitTestingBuildRootPath>` la proprietà viene impostata sul percorso completo di `.vs\...\lut\0\b` . Se il progetto definisce la `<ArtifactsRoot>` proprietà che esegue il mapping al dir della soluzione, è possibile aggiornare il progetto MSBuild come segue:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Percorso dell'artefatto di compilazione

**Si vuole che gli artefatti di Live Unit Testing compilazione vadano in un percorso specifico anziché nel percorso predefinito nella *cartella .vs.* Come è possibile modificare questa impostazione?**

Impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildRoot` sul percorso in cui si vuole che vengano rilasciati gli artefatti di compilazione di Live Unit Testing. 

## <a name="test-explorer-versus-live-unit-testing"></a>Confronto tra Esplora test e Live Unit Testing

**Quali sono le differenze tra l'esecuzione di test dalla finestra Esplora test e l'esecuzione di test in Live Unit Testing?**

Esistono numerose differenze:

- L'esecuzione o il debug di **test dalla** finestra Esplora test esegue file binari normali, Live Unit Testing esegue file binari instrumentati. Se si vuole eseguire il debug di file binari instrumentati, provare ad aggiungere una chiamata al metodo [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) nel metodo di test per fare in modo che il debugger venga avviato ogni volta che si esegue tale metodo (incluso quando viene eseguito da Live Unit Testing). A questo punto è possibile collegare ed eseguire il debug del file binario instrumentato. Ci auguriamo però che le tecniche di strumentazione siano note per la maggior parte degli scenari utente e che non sia necessario eseguire il debug di file binari instrumentati.

- Live Unit Testing crea un nuovo dominio applicazione per eseguire i test,  ma i test eseguiti dalla finestra Esplora test creano un nuovo dominio applicazione.

- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. In **Esplora test** è possibile scegliere di eseguire più test in parallelo.

- **Esplora test** esegue i test in un apartment a thread singolo (STA) per impostazione predefinita, mentre Live Unit Testing esegue i test in un apartment a thread singolo (MTA). Per eseguire test MSTest nell'apartment a thread singolo in Live Unit Testing, decorare il metodo di test o la classe contenitore con l'attributo `<STATestMethod>` o `<STATestClass>` reperibili nel pacchetto NuGet `MSTest.STAExtensions 1.0.3-beta`. Per NUnit e xUnit decorare il metodo di test rispettivamente con l'attributo `<RequiresThread(ApartmentState.STA)>` e con l'attributo `<STAFact>`.

## <a name="exclude-tests"></a>Escludere i test

**Come si escludono i test da Live Unit Testing?**

Per l'impostazione specifica dell'utente, vedere la sezione "Inclusione ed esclusione di progetti e metodi di test" dell'articolo [Usare Live Unit Testing in Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods). L'inclusione o l'esclusione di test è utile quando si vuole eseguire un set specifico di test per una determinata sessione di modifica oppure per rendere persistenti le proprie preferenze personali.

Per le impostazioni specifiche della soluzione è possibile applicare l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> a livello di codice per evitare che metodi, proprietà, classi o strutture vengano instrumentati da Live Unit Testing. È anche possibile impostare la proprietà `<ExcludeFromCodeCoverage>` su `true` nel file di progetto per evitare che l'intero progetto venga instrumentato. Live Unit Testing eseguirà ancora i test non instrumentati, ma le informazioni di code coverage non verranno visualizzate.

È anche possibile verificare se `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` è caricato nel dominio applicazione corrente e disabilitare i test sulla base del motivo corrispondente. Ad esempio, è possibile eseguire quanto segue con xUnit:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Intestazioni PE di Win32

**Perché le intestazioni PE di Win32 sono diverse negli assembly instrumentati compilati da Live Unit Testing?**

Questo problema è stato risolto e non sussiste in Visual Studio 2017 versione 15.3 e versioni successive.

Per le versioni precedenti di Visual Studio 2017, esiste un bug noto che potrebbe impedire alle compilazioni di Live Unit Testing di incorporare i dati seguenti dell'intestazione PE di Win32:

- Versione del file (specificata da @System.Reflection.AssemblyFileVersionAttribute nel codice).

- Icona Win32 (specificata da `/win32icon:` nella riga di comando).

- Manifesto Win32 (specificato da `/win32manifest:` nella riga di comando).

I test che si basano su questi valori potrebbero non riuscire quando vengono eseguiti da Live Unit Testing.

::: moniker-end

## <a name="continuous-builds"></a>Compilazioni continue

**Perché Live Unit Testing continua a compilare la soluzione ogni volta anche se non si apportano modifiche?**

La soluzione può essere compilata anche se non si apportano modifiche se il processo di compilazione genera codice sorgente che fa parte della soluzione stessa e nei file di destinazione della compilazione non sono specificati input e output appropriati. È necessario specificare un elenco di input e di output per le destinazioni in modo che MSBuild possa eseguire i controlli di aggiornamento appropriati e stabilire se è necessaria una nuova compilazione.

Live Unit Testing avvia una compilazione ogni volta che rileva una modifica nei file di origine. Poiché la compilazione della soluzione genera file di origine, Live Unit Testing in un ciclo di compilazione infinito. Se, tuttavia, gli input e gli output della destinazione vengono controllati quando Live Unit Testing avvia la seconda compilazione (dopo aver rilevato i file di origine appena generati dalla compilazione precedente), si interrompe il ciclo di compilazione perché i controlli degli input e degli output indicano che tutto è aggiornato.

## <a name="editor-icons"></a>Icone dell'editor

**Perché non vengono visualizzate icone nell'editor anche se Live Unit Testing sembra che i test siano in esecuzione in base ai messaggi nella finestra Output?**

Questa situazione si verifica se gli assembly su cui Live Unit Testing è in esecuzione non sono instrumentati per un qualsiasi motivo. Live Unit Testing non è ad esempio compatibile con progetti che impostano `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. In questo caso, è necessario aggiornare il processo di compilazione in modo da rimuovere questa impostazione o modificarla in `true` per consentire il corretto funzionamento di Live Unit Testing. 

## <a name="capture-logs"></a>Acquisire i log

**In che modo è possibile raccogliere log più dettagliati per le segnalazioni di bug?**

Per raccogliere log più dettagliati, è possibile eseguire diverse operazioni:

- Passare a **Strumenti**  >  **Opzioni**  >  **Live Unit Testing** e modificare l'opzione di registrazione in **Dettagliato**. in modo che vengano visualizzati log più dettagliati nella **finestra di output**.

- Impostare la variabile di ambiente utente `LiveUnitTesting_BuildLog` sul nome del file da usare per acquisire il log di MSBuild. Sarà quindi possibile recuperare da tale file i messaggi dettagliati del log di MSBuild restituiti da compilazioni di Live Unit Testing.

- Impostare la variabile di ambiente utente `LiveUnitTesting_TestPlatformLog` su `1` per acquisire il log della piattaforma di test. Sarà quindi possibile recuperare i messaggi dettagliati del log della piattaforma di test generati dalle esecuzioni di Live Unit Testing da `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Creare una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e impostarla su 1 (o su un valore qualsiasi) e quindi riavviare Visual Studio. A questo punto dovrebbe essere visualizzata una grande quantità di registrazione nella scheda **Output -** Test in Visual Studio.

## <a name="see-also"></a>Vedi anche

- [Live Unit Testing](live-unit-testing.md)
