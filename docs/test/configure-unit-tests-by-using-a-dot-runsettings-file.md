---
title: Configurare unit test con un file con estensione runsettings
description: Informazioni su come usare il file con estensione runsettings in Visual Studio per configurare unit test eseguiti dalla riga di comando, dall'IDE o in un flusso di lavoro di compilazione.
ms.custom: SEO-VS-2020
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 7fde253ed4bb24c31e8c93b8ce3a5e4290c142ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026824"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurare unit test usando un file *con estensione runsettings*

Gli unit test in Visual Studio possono essere configurati usando un file con estensione *runsettings*. Ad esempio, è possibile modificare la versione di .NET in cui vengono eseguiti i test, la directory dei risultati di test e i dati raccolti durante l'esecuzione dei test. Un uso piuttosto comune di un file con estensione *runsettings* è la personalizzazione dell'[analisi code coverage](../test/customizing-code-coverage-analysis.md).

I file di impostazioni esecuzione test possono essere usati per configurare i test eseguiti dalla riga di [comando,](vstest-console-options.md)dall'IDE o in un [flusso](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) di lavoro di compilazione usando Azure Test Plans o Team Foundation Server (TFS).

I file di impostazioni esecuzione test sono facoltativi. Se non è necessaria alcuna configurazione speciale, non è necessario un file con estensione *runsettings.*

## <a name="create-a-run-settings-file-and-customize-it"></a>Creare un file di impostazioni esecuzione test e personalizzarlo

1. Aggiungere un file di impostazioni esecuzione test alla propria soluzione. In **Esplora soluzioni** scegliere Aggiungi nuovo elemento dal menu di scelta rapida della soluzione e selezionare  >  File **XML.** Salvare il file con un nome, ad esempio *test.runsettings*.

   > [!TIP]
   > Il nome del file non è rilevante, purché si usi l'estensione *runsettings*.

2. Aggiungere il contenuto [del file *.runsettings](#example-runsettings-file)di esempio e quindi personalizzarlo in base alle esigenze, come descritto nelle sezioni seguenti.

3. Specificare il file *.runsettings desiderato usando uno dei metodi seguenti:

   - [IDE di Visual Studio](#specify-a-run-settings-file-in-the-ide)
   - [Riga di comando](#specify-a-run-settings-file-from-the-command-line)
   - [Compilare il](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) flusso di lavoro Azure Test Plans o Team Foundation Server (TFS).

4. Eseguire gli unit test per usare le impostazioni di esecuzione personalizzate.

::: moniker range="vs-2017"

Se si vogliono disattivare e attivare le impostazioni personalizzate nell'IDE, deselezionare o selezionare il file nel menu Test Impostazioni  >  test.

![Menu Impostazioni test con file di impostazioni personalizzato in Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Per disattivare e attivare le impostazioni personalizzate nell'IDE, deselezionare o selezionare il file nel menu **Test.**

::: moniker-end

> [!TIP]
> È possibile creare più file con estensione *runsettings* nella soluzione e selezionarne uno come file di impostazioni test attivo in base alle esigenze.

## <a name="specify-a-run-settings-file-in-the-ide"></a>Specificare un file di impostazioni esecuzione test nell'IDE

I metodi disponibili dipendono dalla versione di Visual Studio.

::: moniker range="vs-2017"
Per specificare un file di impostazioni  esecuzione test nell'IDE, selezionare Test Impostazioni Selezionare il file di Impostazioni test e quindi selezionare il file con estensione >  >  *runsettings.*

![Selezionare il menu di file di impostazioni test in Visual Studio 2017](media/select-test-settings-file.png)

Il file viene visualizzato nel menu Impostazioni test e può essere selezionato o deselezionato. Se selezionato, il file di impostazioni esecuzione test viene applicato ogni volta che si seleziona **Analizza code coverage**.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 versione 16.4 e successive

Esistono tre modi per specificare un file di impostazioni di esecuzione in Visual Studio 2019 versione 16.4 e successive.

- [Rilevamento automatico delle impostazioni esecuzione test](#autodetect-the-run-settings-file)
- [Configurare manualmente le impostazioni di esecuzione](#manually-select-the-run-settings-file)
- [Impostare una proprietà di compilazione](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>Rilevamento automatico del file di impostazioni esecuzione test

> [!NOTE]
> Questa operazione funziona solo per un file denominato `.runsettings` .

Per rilevamento automatico del file di impostazioni esecuzione test, posizionarlo nella radice della soluzione.

Se è abilitato il rilevamento automatico dei file di impostazioni esecuzione test, le impostazioni in questo file vengono applicate a tutti i test eseguiti. È possibile attivare il rilevamento automatico dei file runsettings usando due metodi:

- Selezionare Strumenti **Opzioni** > **Test** >  > **Rileva automaticamente file di impostazioni runsettings**

   ![Opzione rileva automaticamente il file runsettings in Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)

- Selezionare **Test** > **Configura esecuzione Impostazioni** rilevamento automatico file di > **impostazioni**

   ![Menu Rileva automaticamente file runsettings in Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Selezionare manualmente il file di impostazioni esecuzione test

Nell'IDE selezionare **Test** Configure Run Impostazioni Select Solution Wide runsettings File (Seleziona file runsettings a livello di soluzione) e quindi selezionare >  > il file *con estensione runsettings.*

   - Questo file esegue l'override del file con estensione *runsettings* nella radice della soluzione, se presente, e viene applicato a tutti i test eseguiti.
   - Questa selezione di file viene mantenuta solo in locale.

![Selezionare il menu file runsettings a livello di soluzione di test Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Impostare una proprietà di compilazione

Aggiungere una proprietà di compilazione a un progetto tramite il file di progetto o un file Directory.Build.props. Il file di impostazioni di esecuzione per un progetto viene specificato dalla **proprietà RunSettingsFilePath**.

- Project di esecuzione a livello di codice sono attualmente supportate nei progetti C#, VB, C++ e F#.
- Un file specificato per un progetto esegue l'override di qualsiasi altro file di impostazioni esecuzione test specificato nella soluzione.
- [Queste MSBuild proprietà](../msbuild/msbuild-reserved-and-well-known-properties.md) possono essere usate per specificare il percorso del file runsettings.

Esempio di specifica di un file *con estensione runsettings* per un progetto:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 versione 16.3 e precedenti

Per specificare un file di impostazioni esecuzione test nell'IDE, selezionare **Test**  >  **Seleziona Impostazioni file**. Individuare e selezionare il file con estensione *runsettings*.

![Selezionare il menu di file di impostazioni test in Visual Studio 2019](media/vs-2019/select-settings-file.png)

Il file viene visualizzato nel menu Test ed è possibile selezionarlo o deselezionarlo. Se selezionato, il file di impostazioni esecuzione test viene applicato ogni volta che si seleziona **Analizza code coverage**.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Specificare un file di impostazioni di esecuzione dalla riga di comando

Per eseguire test dalla riga di comando, *usarevstest.console.exe* e specificare il file di impostazioni usando il **parametro /Impostazioni** .

1. Aprire [Prompt dei comandi per gli sviluppatori per Visual Studio](../ide/reference/command-prompt-powershell.md).

2. Immettere un comando simile a:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   oppure

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Per altre informazioni, vedere [Opzioni della riga di comando di VSTest.Console.exe](vstest-console-options.md).

## <a name="the-runsettings-file"></a>File *.runsettings

Il file *.runsettings è un file XML che contiene elementi di configurazione diversi all'interno **dell'elemento RunSettings.** Le sezioni che seguono descrivono in dettaglio i diversi elementi. Per un esempio completo, vedere [File *.runsettings di esempio.](#example-runsettings-file)

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Ogni elemento di configurazione è facoltativo perché ha un valore predefinito.

## <a name="runconfiguration-element"></a>Elemento RunConfiguration

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
</RunConfiguration>
```

L'elemento **RunConfiguration** può includere gli elementi seguenti:

|Nodo|Predefinito|Valori|
|-|-|-|
|**MaxCpuCount**|1|Questa impostazione determina il livello di esecuzione parallela dei test durante l'esecuzione di unit test, in base ai core disponibili nel computer. Il motore di esecuzione dei test viene avviato come processo distinto in ogni core disponibile e assegna a ogni core un contenitore con test da eseguire. Un contenitore può essere un assembly, una DLL o un artefatto pertinente. Il contenitore di test è l'unità di pianificazione. In ogni contenitore, i test vengono eseguiti in base al framework di test. Se sono presenti molti contenitori, non appena termina l'esecuzione dei test in un contenitore, i processi vengono assegnati al successivo contenitore disponibile.<br /><br />MaxCpuCount può essere:<br /><br />n, dove 1 < = n < = numero di core: vengono avviati fino a n processi<br /><br />n, dove n = qualsiasi altro valore: il numero di processi avviati può essere fino al numero di core disponibili. Ad esempio, impostare n=0 per consentire alla piattaforma di decidere automaticamente il numero ottimale di processi da avviare in base all'ambiente.|
|**ResultsDirectory**||Directory in cui vengono inseriti i risultati del test. Il percorso è relativo alla directory che contiene il file con estensione runsettings.|
|**Targetframeworkversion**|Framework40|`FrameworkCore10` per le origini .NET Core, `FrameworkUap10` per le origini basate sulla piattaforma UWP, `Framework45` per .NET Framework 4.5 e versioni successive, `Framework40` per .NET Framework 4.0 e `Framework35` per .NET Framework 3.5.<br /><br />Questa impostazione specifica la versione del framework unit test usata per trovare ed eseguire i test. Può essere diversa dalla versione della piattaforma .NET specificata nelle proprietà di compilazione del progetto di unit test.<br /><br />Se si omette l'elemento `TargetFrameworkVersion` dal file con estensione *runsettings*, la piattaforma determina automaticamente la versione del framework sulla base dei file binari compilati.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Uno o più percorsi della directory in cui si trovano i TestAdapter|
|**TestSessionTimeout**||Consente agli utenti di terminare una sessione di test allo scadere di un timeout specificato. L'impostazione di un timeout assicura un consumo ottimale delle risorse e consente di vincolare le sessioni di test a un periodo di tempo stabilito. L'impostazione è disponibile in **Visual Studio 2017 versione 15.5** e versioni successive.|
|**DotnetHostPath**||Specificare un percorso personalizzato per l'host dotnet usato per eseguire il testhost. Ciò è utile quando si compila un dotnet personalizzato, ad esempio quando si compila il repository dotnet/runtime. Se si specifica questa opzione, la ricerca di testhost.exe verrà ignorata e verrà sempre utilizzata la testhost.dll.|
|**TreatNoTestsAsError**|false| true o false <br>Specificare un valore booleano che definisce il codice di uscita quando non vengono individuati test. Se il valore è `true` e non viene individuato alcun test, viene restituito un codice di uscita diverso da zero. In caso contrario, sarà restituito zero.|

## <a name="datacollectors-element-diagnostic-data-adapters"></a>Elemento DataCollectors (adattatori dati di diagnostica)

L'elemento **DataCollectors** specifica le impostazioni degli adattatori dati di diagnostica. Gli adattatori dati di diagnostica raccolgono informazioni aggiuntive sull'ambiente e l'applicazione sottoposta a test. Le impostazioni di ogni adattatore sono predefinite. È quindi necessario specificarle solo se non si vogliono usare quelle predefinite.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>Agente di raccolta dati CodeCoverage

L'agente di raccolta dati di code coverage crea un log in cui le parti del codice dell'applicazione sono state eseguite nel test. Per informazioni dettagliate sulla personalizzazione delle impostazioni per code coverage, vedere [Customize code coverage analysis](../test/customizing-code-coverage-analysis.md).

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
    <CodeCoverage>
      <ModulePaths>
        <Exclude>
          <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
      </ModulePaths>

      <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
      <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
      <CollectFromChildProcesses>True</CollectFromChildProcesses>
      <CollectAspDotNet>False</CollectAspDotNet>
    </CodeCoverage>
  </Configuration>
</DataCollector>
```

### <a name="videorecorder-data-collector"></a>Agente di raccolta dati di VideoRecorder

L'agente di raccolta dati video acquisisce la registrazione di una schermata quando si eseguono i test. La registrazione è utile per la risoluzione dei test dell'interfaccia utente. L'agente di raccolta dati video è disponibile in **Visual Studio 2017 versione 15.5** e versioni successive. Per un esempio di configurazione di questo agente di raccolta dati, vedere il [file *.runsettings di esempio.](#example-runsettings-file)

Per personalizzare qualsiasi altro tipo di adattatore dati di diagnostica, usare un [file di impostazioni di test](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="blame-data-collector"></a>Incolpare l'agente di raccolta dati

Questa opzione consente di isolare un test problematico che causa un arresto anomalo dell'host di test. L'esecuzione dell'agente di raccolta crea un file di output (*Sequence.xml*) in *TestResults*, che acquisisce l'ordine di esecuzione del test prima dell'arresto anomalo del sistema.

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

I parametri di esecuzione dei test consentono di definire variabili e valori disponibili per i test in fase di esecuzione. Accedere ai parametri usando la proprietà MSTest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> (o NUnit [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)):

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Per usare i parametri di esecuzione dei test, aggiungere una <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> proprietà pubblica alla classe di test.

## <a name="loggerrunsettings-element"></a>Elemento LoggerRunSettings

La `LoggerRunSettings` sezione definisce uno o più logger da usare per l'esecuzione dei test. I logger più comuni sono console, Visual Studio Risultati test File (trx) e html.

```xml
<LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>Elemento MSTest

Queste impostazioni sono specifiche dell'adattatore di test che esegue i metodi di test con l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

|Configurazione|Predefinito|Valori|
|-|-|-|
|**ForcedLegacyMode**|false|In Visual Studio 2012, l'adapter MSTest è stato ottimizzato per essere più veloce e più scalabile. Un comportamento, ad esempio l'ordine in cui vengono eseguiti i test, potrebbe non essere esattamente come quello nelle versioni precedenti di Visual Studio. Impostare questo valore su **true** per usare l'adattatore di test precedente.<br /><br />Lo si può usare, ad esempio, nel caso in cui sia presente un file *app.config* specificato per uno unit test.<br /><br />È consigliabile provare a effettuare il refactoring dei test per consentire l'uso dell'adattatore più recente.|
|**IgnoreTestImpact**|false|La funzionalità di impatto sui test assegna la priorità ai test interessati dalle modifiche recenti, quando vengono eseguiti in MSTest o da Microsoft Test Manager (deprecati in Visual Studio 2017). Questa impostazione disattiva la funzionalità. Per altre informazioni, vedere [Test da eseguire da una compilazione precedente](/previous-versions/dd286589(v=vs.140)).|
|**SettingsFile**||È possibile specificare un file di impostazioni test da usare con l'adattatore MSTest. È anche possibile specificare un file di impostazioni test [dal menu delle impostazioni](#specify-a-run-settings-file-in-the-ide).<br /><br />Se si specifica questo valore, è necessario impostare anche **ForcedlegacyMode** su **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Una volta completata l'esecuzione di un test, MSTest viene arrestato. Anche qualsiasi processo avviato come parte del test verrà interrotto. Per fare in modo che l'executor di test rimanga attivo, impostare questa configurazione su **true**. Lo si può usare, ad esempio, per mantenere in esecuzione il browser tra i test codificati dell'interfaccia utente.|
|**DeploymentEnabled**|true|Se si imposta il valore su **false**, gli elementi della distribuzione specificati nel metodo di test non vengono copiati nella directory di distribuzione.|
|**CaptureTraceOutput**|true|È possibile scrivere nella traccia di debug dal metodo di test usando <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Per mantenere la directory di distribuzione dopo un'esecuzione di test, impostare questo valore su **false**.|
|**MapInconclusiveToFailed**|false|Se un test viene completato senza risultati, ne viene eseguito il mapping allo stato Ignorato in **Esplora test**. Se si vuole che i test senza risultati vengano visualizzati come non superati, impostare il valore su **true**.|
|**InProcMode**|false|Per fare in modo che i test vengano eseguiti nello stesso processo dell'adattatore MSTest, impostare questo valore su **true**. Questa impostazione fornisce un lieve miglioramento delle prestazioni. Ma se un test termina con un'eccezione, i test rimanenti non vengono eseguiti.|
|**AssemblyResolution**|false|È possibile specificare i percorsi di assembly aggiuntivi durante la ricerca e l'esecuzione di unit test. Ad esempio, è possibile usare questi percorsi per gli assembly di dipendenza che non si trovano nella stessa directory dell'assembly di test. Per specificare un percorso, usare un elemento **Directory Path**. I percorsi possono includere variabili di ambiente.<br /><br />`<AssemblyResolution>  <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>File *con estensione runsettings di* esempio

Il codice XML seguente rappresenta il contenuto di un tipico file con estensione *runsettings*. Copiare questo codice e modificarlo in base alle esigenze.

Ogni elemento del file è facoltativo perché usa un valore predefinito.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>

    <!-- true or false -->
    <!-- Value that specifies the exit code when no tests are discovered -->
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="specify-environment-variables-in-the-runsettings-file"></a>Specificare le variabili di ambiente nel file *con estensione runsettings*

Le variabili di ambiente possono essere impostate nel file *con estensione runsettings,* che può interagire direttamente con l'host di test. La specifica di variabili di ambiente nel file con estensione *runsettings* è necessaria per supportare progetti non locali che richiedono l'impostazione di variabili di ambiente *come DOTNET_ROOT*. Queste variabili vengono impostate durante la generazione del processo host di test e sono disponibili nell'host.

### <a name="example"></a>Esempio

Il codice seguente è un file con estensione *runsettings* di esempio che passa le variabili di ambiente:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

Il **nodo RunConfiguration** deve contenere un **nodo EnvironmentVariables.** Una variabile di ambiente può essere specificata come nome di elemento e il relativo valore.

> [!NOTE]
> Poiché queste variabili di ambiente devono essere sempre impostate all'avvio dell'host di test, i test devono sempre essere eseguiti in un processo separato. A questo scopo, il flag */InIsolation* verrà impostato quando sono presenti variabili di ambiente in modo che l'host di test sia sempre richiamato.

## <a name="see-also"></a>Vedi anche

- [Configurare un agente di test](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md)
- [Attività di test di Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts&preserve-view=true)
