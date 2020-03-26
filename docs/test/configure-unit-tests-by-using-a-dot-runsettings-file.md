---
title: Configurare unit test con un file con estensione runsettings
ms.date: 10/03/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: cad3a644935e14a605dbef02bddc1f9337c1f5e9
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233089"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configurare unit test utilizzando un file *con estensione runsettings*

Gli unit test in Visual Studio possono essere configurati usando un file con estensione *runsettings*. Ad esempio, è possibile modificare la versione di .NET in cui vengono eseguiti i test, la directory dei risultati di test e i dati raccolti durante l'esecuzione dei test.

I file di impostazioni esecuzione test sono facoltativi. Se non è necessaria alcuna configurazione speciale, non è necessario un file *con estensione runsettings.* Un uso piuttosto comune di un file con estensione *runsettings* è la personalizzazione dell'[analisi code coverage](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Specificare un file di impostazioni esecuzione test

I file di impostazioni esecuzione test possono essere usati per configurare i test eseguiti dalla [riga di comando](vstest-console-options.md), nell'IDE o in un [flusso di lavoro di compilazione](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) usando Azure Test Plans o Team Foundation Server (TFS).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Per specificare un file di impostazioni esecuzione test, selezionare **Test** > **Impostazioni test** > **Seleziona file di impostazioni test** e quindi selezionare il file con estensione *runsettings*.

![Selezionare il menu di file di impostazioni test in Visual Studio 2017](media/select-test-settings-file.png)

Il file viene visualizzato nel menu Impostazioni test e può essere selezionato o deselezionato. Se selezionato, il file di impostazioni esecuzione test viene applicato ogni volta che si seleziona **Analizza code coverage**.

::: moniker-end

::: moniker range=">=vs-2019"

#### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 versione 16.3 e precedenti

Per specificare un file di impostazioni esecuzione nell'IDE, selezionare **Test seleziona** > **file di impostazioni**. Individuare e selezionare il file con estensione *runsettings*.

![Selezionare il menu di file di impostazioni test in Visual Studio 2019](media/vs-2019/select-settings-file.png)

Il file viene visualizzato nel menu Test ed è possibile selezionarlo o deselezionarlo. Se selezionato, il file di impostazioni esecuzione test viene applicato ogni volta che si seleziona **Analizza code coverage**.

#### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 versione 16.4 e successive

Esistono tre modi per specificare un file di impostazioni di esecuzione in Visual Studio 2019 versione 16.4 e successive:There are three ways of specifying a run settings file in Visual Studio 2019 version 16.4 and later:

- Aggiungere una proprietà di compilazione a un progetto tramite il file di progetto o un file Directory.Build.props.Add a build property to a project through either the project file or a Directory.Build.props file. Il file delle impostazioni di esecuzione per un progetto è specificato dalla proprietà **RunSettingsFilePath**.

    - Le impostazioni di esecuzione a livello di progetto sono attualmente supportate nei progetti In C, VB, C' e F.
    - Un file specificato per un progetto esegue l'override di qualsiasi altro file di impostazioni esecuzione specificato nella soluzione.
    - [Queste proprietà MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) possono essere utilizzate per specificare il percorso del file runsettings. 

    Esempio di specifica di un file *.runsettings* per un progetto:
    
    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
      </PropertyGroup>
      ...
    </Project>
    ```

- Inserire un file di impostazioni di esecuzione denominato ".runsettings" nella radice della soluzione.

  Se il rilevamento automatico dei file delle impostazioni di esecuzione è abilitato, le impostazioni in questo file vengono applicate a tutti i test eseguiti. È possibile attivare il rilevamento automatico dei file runsettings da due posizioni:
  
    - **Strumenti** > **Opzioni** > **Test Rileva** > **automaticamente runsettings File**

      ![Opzione del file di rilevamento automatico runsettings in Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
    - **Test** > **Configurare Le impostazioni** > di esecuzione **Rileva automaticamente i file runsettings**
    
      ![Menu del file di rilevamento automatico delle impostazioni runsettings in Visual Studio 2019Auto detect runsettings file menu in Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

- Nell'IDE selezionare **Test** > **Configura impostazioni esecuzione impostazioni** > **Selezionare File runsettings**di Soluzione , quindi selezionare il file *con estensione runsettings.*

   ![Selezionare il menu del file di impostazioni di esecuzione a livello di soluzione di test in Visual Studio 2019Select solution-wide runsettings file menu in Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)
      
   - Questo file esegue l'override del file ".runsettings" nella radice della soluzione, se presente, e viene applicato in tutti i test eseguiti.  
   - Questa selezione di file viene mantenuta solo localmente. 

::: moniker-end

### <a name="command-line"></a>Riga di comando

Per eseguire test dalla riga di comando, utilizzare *vstest.console.exe*e specificare il file delle impostazioni utilizzando il parametro **/Settings.**

1. Avviare il prompt dei comandi di Visual Studio Developer:

   ::: moniker range="vs-2017"

   Nel menu **Start** di Windows scegliere **Visual Studio 2017** > **Prompt dei comandi per gli sviluppatori per VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Nel menu **Start** di Windows scegliere **Visual Studio 2019** > **Prompt dei comandi per gli sviluppatori per VS 2019**.

   ::: moniker-end

2. Immettere un comando simile a:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   o

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Per altre informazioni, vedere [Opzioni della riga di comando di VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Personalizzare i test

Per personalizzare i test usando un file con estensione *runsettings*, seguire questa procedura:

1. Aggiungere un file XML alla soluzione di Visual Studio e salvarlo come *test.runsettings*.

   > [!TIP]
   > Il nome del file non è rilevante, purché si usi l'estensione *runsettings*.

2. Sostituire il contenuto del file con il codice XML dell'esempio riportato di seguito e personalizzarlo in base alle esigenze.

::: moniker range="vs-2017"

3. Nel menu **Test** scegliere **Impostazioni test** > **Seleziona file di impostazioni test**. Selezionare il file con estensione *runsettings* creato e quindi selezionare **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Per selezionare il file delle impostazioni di esecuzione, scegliere File di**selezione** **test** > . Selezionare il file con estensione *runsettings* creato e quindi selezionare **OK**.

::: moniker-end

   > [!TIP]
   > È possibile creare più file con estensione *runsettings* nella soluzione e selezionarne uno come file di impostazioni test attivo in base alle esigenze.

## <a name="example-runsettings-file"></a>Esempio di file *.runsettings*

Il codice XML seguente rappresenta il contenuto di un tipico file con estensione *runsettings*. Ogni elemento del file è facoltativo perché usa un valore predefinito.

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
    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

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

## <a name="elements-of-a-runsettings-file"></a>Elementi di un file con estensione *runsettings*

Le sezioni che seguono descrivono in dettaglio gli elementi di un file con estensione *runsettings*.

### <a name="run-configuration"></a>Configurazione di esecuzione

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

L'elemento **RunConfiguration** può includere gli elementi seguenti:

|Nodo|Predefinito|Valori|
|-|-|-|
|**ResultsDirectory**||Directory in cui vengono inseriti i risultati del test.|
|**Targetframeworkversion**|Framework40|`FrameworkCore10` per le origini .NET Core, `FrameworkUap10` per le origini basate sulla piattaforma UWP, `Framework45` per .NET Framework 4.5 e versioni successive, `Framework40` per .NET Framework 4.0 e `Framework35` per .NET Framework 3.5.<br /><br />Questa impostazione specifica la versione del framework unit test usata per trovare ed eseguire i test. Può essere diversa dalla versione della piattaforma .NET specificata nelle proprietà di compilazione del progetto di unit test.<br /><br />Se si omette l'elemento `TargetFrameworkVersion` dal file con estensione *runsettings*, la piattaforma determina automaticamente la versione del framework sulla base dei file binari compilati.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Uno o più percorsi della directory in cui si trovano i TestAdapter|
|**MaxCpuCount**|1|Questa impostazione determina il livello di esecuzione parallela dei test durante l'esecuzione di unit test, in base ai core disponibili nel computer. Il motore di esecuzione dei test viene avviato come processo distinto in ogni core disponibile e assegna a ogni core un contenitore con test da eseguire. Un contenitore può essere un assembly, una DLL o un artefatto pertinente. Il contenitore di test è l'unità di pianificazione. In ogni contenitore, i test vengono eseguiti in base al framework di test. Se sono presenti molti contenitori, non appena termina l'esecuzione dei test in un contenitore, i processi vengono assegnati al successivo contenitore disponibile.<br /><br />MaxCpuCount può essere:<br /><br />n, dove 1 < = n < = numero di core: vengono avviati fino a n processi<br /><br />n, dove n - qualsiasi altro valore: il numero di processi avviati può essere fino al numero di core disponibili. Ad esempio, impostare n-0 per consentire alla piattaforma di decidere automaticamente il numero ottimale di processi da avviare in base all'ambiente.|
|**TestSessionTimeout**||Consente agli utenti di terminare una sessione di test allo scadere di un timeout specificato. L'impostazione di un timeout assicura un consumo ottimale delle risorse e consente di vincolare le sessioni di test a un periodo di tempo stabilito. L'impostazione è disponibile in **Visual Studio 2017 versione 15.5** e versioni successive.|
|**Percorso di dotnetHost**||Specificare un percorso personalizzato per l'host dotnet utilizzato per eseguire testhost. Ciò è utile quando si compila un proprio dotnet, ad esempio quando si compila il repository dotnet/runtime. Specificando questa opzione salterà la ricerca di testhost.exe e utilizzerà sempre il file testhost.dll. 

### <a name="diagnostic-data-adapters-data-collectors"></a>Adattatori dati di diagnostica (agenti di raccolta dati)

L'elemento **DataCollectors** specifica le impostazioni degli adattatori dati di diagnostica. Gli adattatori dati di diagnostica raccolgono informazioni aggiuntive sull'ambiente e l'applicazione sottoposta a test. Le impostazioni di ogni adattatore sono predefinite. È quindi necessario specificarle solo se non si vogliono usare quelle predefinite.

#### <a name="code-coverage-adapter"></a>Adattatore di code coverage

```xml
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
```

L'agente di raccolta dati di code coverage crea un log in cui le parti del codice dell'applicazione sono state eseguite nel test. Per altre informazioni sulla personalizzazione delle impostazioni per il code coverage, vedere [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Agente di raccolta dati video

L'agente di raccolta dati video acquisisce la registrazione di una schermata quando si eseguono i test. La registrazione è utile per la risoluzione dei test dell'interfaccia utente. L'agente di raccolta dati video è disponibile in **Visual Studio 2017 versione 15.5** e versioni successive.

Per personalizzare qualsiasi altro tipo di adattatore dati di diagnostica, usare un [file di impostazioni di test](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

I parametri di esecuzione dei test consentono di definire variabili e valori disponibili per i test in fase di esecuzione. Accedere ai parametri usando la proprietà <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Per usare i parametri di esecuzione dei test, aggiungere un campo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> privato e una proprietà <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pubblica alla classe di test.

### <a name="mstest-run-settings"></a>Impostazioni di esecuzione MSTest

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Queste impostazioni sono specifiche dell'adattatore di test che esegue i metodi di test con l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

|Configurazione|Predefinito|Valori|
|-|-|-|
|**ForcedLegacyMode**|false|In Visual Studio 2012, l'adapter MSTest è stato ottimizzato per essere più veloce e più scalabile. Un comportamento, ad esempio l'ordine in cui vengono eseguiti i test, potrebbe non essere esattamente come quello nelle versioni precedenti di Visual Studio. Impostare questo valore su **true** per usare l'adattatore di test precedente.<br /><br />Lo si può usare, ad esempio, nel caso in cui sia presente un file *app.config* specificato per uno unit test.<br /><br />È consigliabile provare a effettuare il refactoring dei test per consentire l'uso dell'adattatore più recente.|
|**IgnoreTestImpact**|false|La funzionalità dell'impatto sui test assegna la priorità ai test interessati da modifiche recenti, una volta eseguiti in MSTest o da Microsoft Test Manager. Questa impostazione disattiva la funzionalità. Per altre informazioni, vedere [Test da eseguire da una compilazione precedente](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||È possibile specificare un file di impostazioni test da usare con l'adattatore MSTest. È anche possibile specificare un file di impostazioni test [dal menu delle impostazioni](#ide).<br /><br />Se si specifica questo valore, è necessario impostare anche **ForcedlegacyMode** su **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|Una volta completata l'esecuzione di un test, MSTest viene arrestato. Anche qualsiasi processo avviato come parte del test verrà interrotto. Per fare in modo che l'executor di test rimanga attivo, impostare questa configurazione su **true**. Lo si può usare, ad esempio, per mantenere in esecuzione il browser tra i test codificati dell'interfaccia utente.|
|**DeploymentEnabled**|true|Se si imposta il valore su **false**, gli elementi della distribuzione specificati nel metodo di test non vengono copiati nella directory di distribuzione.|
|**CaptureTraceOutput**|true|È possibile scrivere nella traccia di debug dal metodo di test usando <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Per mantenere la directory di distribuzione dopo un'esecuzione di test, impostare questo valore su **false**.|
|**MapInconclusiveToFailed**|false|Se un test viene completato senza risultati, ne viene eseguito il mapping allo stato Ignorato in **Esplora test**. Se si vuole che i test senza risultati vengano visualizzati come non superati, impostare il valore su **true**.|
|**InProcMode**|false|Per fare in modo che i test vengano eseguiti nello stesso processo dell'adattatore MSTest, impostare questo valore su **true**. Questa impostazione fornisce un lieve miglioramento delle prestazioni. Ma se un test termina con un'eccezione, i test rimanenti non vengono eseguiti.|
|**AssemblyResolution**|false|È possibile specificare i percorsi di assembly aggiuntivi durante la ricerca e l'esecuzione di unit test. Ad esempio, è possibile usare questi percorsi per gli assembly di dipendenza che non si trovano nella stessa directory dell'assembly di test. Per specificare un percorso, usare un elemento **Directory Path**. I percorsi possono includere variabili di ambiente.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Vedere anche

- [Configurare un agente di test](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personalizzare l'analisi code coverage](../test/customizing-code-coverage-analysis.md)
- [Attività di test di Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)

