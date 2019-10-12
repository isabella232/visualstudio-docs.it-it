---
title: Domande frequenti su Live Unit Testing
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: gewarren
ms.author: gewarren
ms.workload:
- dotnet
ms.openlocfilehash: 545c8974e3d0dea196a6168db03586a37d15ed72
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262286"
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

Se sono presenti progetti di test basati su MSTest precedenti che fanno riferimento a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e non si vuole passare ai pacchetti NuGet di MSTest più recenti, eseguire l'aggiornamento a Visual Studio 2019 o Visual Studio 2017.

In alcuni casi, per consentire il funzionamento di Live Unit Testing, potrebbe essere necessario ripristinare in modo esplicito i pacchetti NuGet a cui viene fatto riferimento nei progetti della soluzione. È possibile ripristinare i pacchetti eseguendo una compilazione esplicita della soluzione (selezionare **compila** > **Ricompila soluzione** dal menu di primo livello di Visual Studio) o facendo clic con il pulsante destro del mouse sulla soluzione e selezionando **Ripristina pacchetti NuGet** . prima di abilitare Living unit testing.

## <a name="net-core-support"></a>Supporto di .NET Core

**Live Unit Testing è compatibile con .NET Core?**

Sì. Live Unit Testing funziona con .NET Core e .NET Framework.

## <a name="configuration"></a>Configurazione

**Perché Live Unit Testing non funziona quando viene attivato?**

La finestra di output (quando è selezionato l'elenco a discesa Live Unit Testing) indica il motivo per cui Live Unit Testing non funziona. È possibile che Live Unit Testing non funzioni per uno dei motivi seguenti:

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

- Assicurarsi che anche il file MSBuild con estensione *props* importato dal pacchetto dell'adattatore di test sia stato aggiornato correttamente. Controllare la versione o il percorso del pacchetto NuGet importato indicato in genere nella parte superiore del file di progetto, come illustrato di seguito:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Personalizzare le compilazioni

**È possibile personalizzare le compilazioni di Live Unit Testing?**

Se per eseguire la compilazione per la strumentazione (Live Unit Testing) la soluzione richiede istruzioni personalizzate che non sono necessarie per la compilazione normale non instrumentata, è possibile aggiungere ai file di progetto o con estensione *target* codice che verifica la presenza della proprietà `BuildingForLiveUnitTesting` ed esegue le istruzioni personalizzate di pre/post-compilazione. È anche possibile scegliere di rimuovere alcune istruzioni di compilazione, ad esempio per la pubblicazione o la creazione di pacchetti, o di aggiungere istruzioni di compilazione, ad esempio per la copia dei prerequisiti, a una compilazione di Live Unit Testing in base a questa proprietà del progetto. La personalizzazione della compilazione basata su questa proprietà non altera in alcun modo la compilazione normale e influisce solo sulle compilazioni di Live Unit Testing.

Ad esempio, potrebbe essere presente una destinazione che produce pacchetti NuGet durante una compilazione normale. È probabile che non si vogliano generare pacchetti NuGet dopo ogni modifica apportata. È quindi possibile disabilitare tale destinazione nella compilazione di Live Unit Testing eseguendo quanto segue:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-or-outdir"></a>Messaggi di errore con \<OutputPath > o \<OutDir >

**Perché quando Live Unit Testing prova a compilare la soluzione viene visualizzato l'errore "...sembra impostato in modo incondizionato su `<OutputPath>` o `<OutDir>`. In Live Unit Testing non verranno eseguiti test dall'assembly di output"?**

Questo errore può verificarsi se il processo di compilazione per la soluzione esegue in modo incondizionato l'override di `<OutputPath>` o `<OutDir>` in modo tale che non sia una sottodirectory di `<BaseOutputPath>`. In tali casi Live Unit Testing non funziona, perché esegue anche l'override di questi elementi per assicurarsi che gli artefatti di compilazione vengano rilasciati in una cartella in `<BaseOutputPath>`. Se è necessario eseguire l'override del percorso devono essere rilasciati gli artefatti di compilazione in una compilazione normale, eseguire l'override di `<OutputPath>` in modo condizionale in base a `<BaseOutputPath>`.

Se ad esempio la compilazione esegue l'override di `<OutputPath>` come illustrato di seguito:

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

## <a name="build-artifact-location"></a>Percorso artefatto di compilazione

**Si vogliono impostare gli artefatti di una compilazione di Live Unit Testing in modo che vengano rilasciati in un percorso specifico invece di quello predefinito nella cartella *vs*. Come si può modificare questa impostazione?**

Impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildRoot` sul percorso in cui si vuole che vengano rilasciati gli artefatti di compilazione di Live Unit Testing. 

## <a name="test-explorer-versus-live-unit-testing"></a>Esplora test rispetto a Live Unit Testing

**Quali sono le differenze tra l'esecuzione di test dalla finestra Esplora test e l'esecuzione di test in Live Unit Testing?**

Esistono numerose differenze:

- Durante l'esecuzione o il debug di test nella finestra **Esplora test** vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati. Se si vuole eseguire il debug di file binari instrumentati, provare ad aggiungere una chiamata al metodo [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch)  nel metodo di test per fare in modo che il debugger venga avviato ogni volta che si esegue tale metodo (incluso quando viene eseguito da Live Unit Testing). A questo punto, è possibile collegare ed eseguire il debug del file binario instrumentato. Ci auguriamo però che le tecniche di strumentazione siano note per la maggior parte degli scenari utente e che non sia necessario eseguire il debug di file binari instrumentati.

- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma i test vengono eseguiti dalla finestra **Esplora test** per creare un nuovo dominio applicazione.

- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. In **Esplora test**è possibile scegliere di eseguire più test in parallelo.

- Per l'individuazione e l'esecuzione di test in Live Unit Testing viene usata la versione 2 di `TestPlatform`, mentre nella finestra **Esplora test** viene usata la versione 1. Nella maggior parte dei casi non si dovrebbero notare differenze.

- **Esplora test** esegue i test in un Apartment a thread singolo (sta) per impostazione predefinita, mentre Live unit testing esegue i test in un Apartment a thread multipli (MTA). Per eseguire test MSTest nell'apartment a thread singolo in Live Unit Testing, decorare il metodo di test o la classe contenitore con l'attributo `<STATestMethod>` o `<STATestClass>` reperibili nel pacchetto NuGet `MSTest.STAExtensions 1.0.3-beta`. Per NUnit e xUnit decorare il metodo di test rispettivamente con l'attributo `<RequiresThread(ApartmentState.STA)>` e con l'attributo `<STAFact>`.

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

La soluzione può essere compilata anche se non vengono apportate modifiche se il processo di compilazione genera codice sorgente che fa parte della soluzione stessa e se i file di destinazione della compilazione non dispongono di input e output appropriati specificati. È necessario specificare un elenco di input e di output per le destinazioni in modo che MSBuild possa eseguire i controlli di aggiornamento appropriati e stabilire se è necessaria una nuova compilazione.

Live Unit Testing avvia una compilazione ogni volta che rileva una modifica nei file di origine. Poiché la compilazione della soluzione genera file di origine, Live Unit Testing entra in un ciclo di compilazione infinito. Se, tuttavia, gli input e gli output della destinazione vengono controllati quando Live Unit Testing avvia la seconda compilazione (dopo aver rilevato i file di origine appena generati dalla compilazione precedente), si interrompe il ciclo di compilazione perché i controlli di input e output indicano che tutti gli elementi sono aggiornati.

## <a name="editor-icons"></a>Icone dell'editor

**Perché nell'editor non sono presenti icone anche se Live Unit Testing sembra eseguire i test in base ai messaggi nella finestra di output?**

Questa situazione si verifica se gli assembly su cui Live Unit Testing è in esecuzione non sono instrumentati per un qualsiasi motivo. Live Unit Testing non è ad esempio compatibile con progetti che impostano `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. In questo caso, è necessario aggiornare il processo di compilazione in modo da rimuovere questa impostazione o modificarla in `true` per consentire il corretto funzionamento di Live Unit Testing. 

## <a name="capture-logs"></a>Acquisire i log

**In che modo è possibile raccogliere log più dettagliati per le segnalazioni di bug?**

Per raccogliere log più dettagliati, è possibile eseguire diverse operazioni:

- Passare a **Strumenti** > **Opzioni** > **Live Unit Testing** e impostare l'opzione del livello di registrazione su **Dettagliato**, in modo che vengano visualizzati log più dettagliati nella **finestra di output**.

- Impostare la variabile di ambiente utente `LiveUnitTesting_BuildLog` sul nome del file da usare per acquisire il log di MSBuild. Sarà quindi possibile recuperare da tale file i messaggi dettagliati del log di MSBuild restituiti da compilazioni di Live Unit Testing.

- Impostare la variabile di ambiente utente `LiveUnitTesting_TestPlatformLog` su `1` per acquisire il log della piattaforma di test. Sarà quindi possibile recuperare i messaggi dettagliati del log della piattaforma di test generati dalle esecuzioni di Live Unit Testing da `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Creare una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e impostarla su 1 (o su un valore qualsiasi) e quindi riavviare Visual Studio. A questo punto verranno visualizzati molti più messaggi di registrazione nella scheda **Output - Test** di Visual Studio.

## <a name="see-also"></a>Vedere anche

- [Live Unit Testing](live-unit-testing.md)
