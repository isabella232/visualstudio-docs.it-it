---
title: Personalizzare la compilazione | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7ddf87f5fa9f937c0272e37f3a6b4aba29f2d6c
ms.sourcegitcommit: a80489d216c4316fde2579a0a2d7fdb54478abdf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652794"
---
# <a name="customize-your-build"></a>Personalizzare la compilazione

I progetti MSBuild che usano il processo di compilazione standard, vale a dire l'importazione di *Microsoft.Common.props* e *Microsoft.Common.targets*, possono usare diversi hook di estensibilità per personalizzare il processo di compilazione.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Aggiungere argomenti alle chiamate di MSBuild da riga di comando per il progetto

Il file *Directory.Build.rsp* contenuto nella directory di origine o in una directory superiore viene applicato alle compilazioni da riga di comando del progetto. Per informazioni dettagliate, vedere [File di risposta MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props e Directory.Build.targets

Nelle versioni di MS Build precedenti alla 15, per specificare una nuova proprietà personalizzata per i progetti nella soluzione, è necessario aggiungere manualmente un riferimento a tale proprietà per ogni file di progetto della soluzione. Oppure, è necessario definire la proprietà in un file *PROPS* e quindi importare in modo esplicito il file *PROPS* in ogni progetto della soluzione, tra le altre cose.

Ora è tuttavia possibile aggiungere una nuova proprietà a ogni progetto in un unico passaggio, definendola in un singolo file denominato *Directory.Build.props* nella cartella radice che contiene l'origine. Quando si esegue MSBuild, *Microsoft.Common.props* cerca la struttura di directory per il file *Directory.Build.props* (e *MicrosoftCommon.targets* cerca *Directory.Build.targets*). Se trova la struttura, importa la proprietà. *Directory.Build.props* è un file definito dall'utente che specifica le personalizzazioni dei progetti in una directory.

> [!NOTE]
> I file system basati su Linux fanno distinzione tra maiuscole e minuscole. Assicurarsi che le maiuscole e minuscole del nome file Directory.Build.props corrispondano esattamente o il file non verrà rilevato durante il processo di compilazione.
>
> Per altre informazioni, vedere [questo problema in GitHub](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Esempio di Directory.Build.props

Ad esempio, per consentire a tutti i progetti di accedere alla nuova funzionalità di Roslyn **/deterministic** (esposta nella destinazione `CoreCompile` di Roslyn dalla proprietà `$(Deterministic)`), è possibile eseguire le operazioni indicate di seguito.

1. Creare un nuovo file nella radice del repository denominato *Directory.Build.props*.
2. Aggiungere al file il seguente codice XML.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Eseguire MSBuild. Le importazioni esistenti del progetto di *Microsoft.Common.props* e *Microsoft.Common.targets* trovano il file e lo importano.

### <a name="search-scope"></a>Ambito di ricerca

Quando cerca un file *Directory.Build.props*, MSBuild scorre la struttura di directory verso l'alto a partire dalla posizione del progetto (`$(MSBuildProjectFullPath)`), fermandosi quando individua un file *Directory.Build.props*. Ad esempio, se `$(MSBuildProjectFullPath)` è *c:\users\nomeutente\code\test\case1*, MSBuild inizia a cercare da quel punto ed esegue la ricerca nella struttura di directory verso l'alto finché non trova un file *Directory.Build.props*, come nella struttura di directory riportata di seguito.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

La posizione del file della soluzione è irrilevante per *Directory.Build.props*.

### <a name="import-order"></a>Ordine di importazione

*Directory.Build.props* viene importato molto presto in *Microsoft.Common.props* e le proprietà definite in un secondo tempo non sono disponibili per questo file. Quindi, evitare di fare riferimento a proprietà che non sono ancora state definite (e verranno restituite come vuote).

*Directory.Build.targets* viene importato da *Microsoft.Common.targets* dopo l'importazione dei file *.targets* dai pacchetti NuGet. Può quindi eseguire l'override di proprietà e destinazioni definite nella maggior parte della logica di compilazione, ma a volte può essere necessario personalizzare il file di progetto dopo l'importazione finale.

### <a name="use-case-multi-level-merging"></a>Caso d'uso: unione a più livelli

Si supponga di avere questa struttura della soluzione standard:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Potrebbe essere preferibile usare proprietà comuni per tutti i progetti *(1)* , proprietà comuni per i progetti *src* *(2-src)* e proprietà comuni per i progetti *test* *(2-test)* .

Per consentire a MSBuild di unire correttamente i file "interni"(*2-src* e *2-test*) e il file "esterno" (*1*), è necessario tenere presente che quando MSBuild trova un file *Directory.Build.props*, interrompe l'analisi. Per continuare l'analisi e completare l'unione con il file esterno, inserire questo codice in entrambi i file interni:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

L'approccio generale di MSBuild può essere riepilogato come segue:

- Per ogni progetto, MSBuild trova il primo file *Directory.Build.props* procedendo verso l'alto nella struttura della soluzione, lo unisce ai valori predefiniti e interrompe l'analisi
- Se si vogliono rilevare e unire più livelli, usare [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (illustrato in precedenza) per importare il file "esterno" dal file "interno"
- Se il file "esterno" non importa a sua volta un elemento situato a un livello superiore, l'analisi si interrompe qui
- Per controllare il processo di analisi/unione, usare `$(DirectoryBuildPropsPath)` e `$(ImportDirectoryBuildProps)`

O più semplicemente: il primo file *Directory.Build.props* che non esegue alcuna importazione è il punto in cui MSBuild si arresta.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Scegliere se aggiungere proprietà a un file con estensione props o target

MSBuild si basa sull'ordine di importazione e l'ultima definizione di una proprietà (o un `UsingTask` o una destinazione) diventa l'ultima definizione usata.

Quando si usano importazioni esplicite, è possibile importare da un file *.props* o *.targets* in qualsiasi momento. Di seguito è illustrata la convenzione più diffusa:

- I file con estensione *props* vengono importati nella fase iniziale e sono inclusi nell'ordine di importazione.

- I file con estensione *targets* vengono importati nelle fasi conclusive e sono inclusi nell'ordine di compilazione.

Questa convenzione viene applicata dai processi di importazione `<Project Sdk="SdkName">` (ovvero, per prima cosa viene eseguita l'importazione di *Sdk.props*, prima di tutti i contenuti del file, e quindi viene importato *Sdk.targets*, dopo tutti i contenuti del file).

Prima di decidere a quale tipo di file aggiungere le proprietà, usare le linee guida generali seguenti:

- Per molte proprietà, non è importante la posizione in cui vengono definite, in quanto non vengono sovrascritte e, in fase di esecuzione, sono di sola lettura.

- Nel caso in cui sia necessario personalizzare il comportamento in un singolo progetto, impostare i valori predefiniti nel file *props*.

- Evitare di impostare proprietà dipendenti nei file *props* leggendo il valore di una proprietà potenzialmente personalizzata, poiché la personalizzazione verrà eseguita solo nel momento in cui MSBuild leggerà il progetto dell'utente.

- Impostare proprietà dipendenti nei file *targets*, poiché acquisiranno le personalizzazioni dai singoli progetti.

- Se è necessario eseguire l'override delle proprietà, eseguire questa operazione in un file *targets*, dopo che sarà stato possibile applicare tutte le personalizzazioni dei progetti definiti dagli utenti. Prestare attenzione quando si usano proprietà derivate, poiché potrebbe essere necessario eseguire l'override anche di esse.

- Includere elementi nei file *props* (usando una condizione basata su una proprietà). Tutte le proprietà verranno considerate prima di qualsiasi elemento, in modo che vengano applicate tutte le personalizzazioni di proprietà definite nei progetti definiti dagli utenti e in questi sia quindi possibile eseguire l'operazione `Remove` o `Update` su qualsiasi elemento aggiunto tramite l'importazione.

- Definire le destinazioni nei file *targets*. Se, tuttavia, il file *targets* viene importato da un SDK, l'esecuzione dell'override della destinazione risulterà più difficile, poiché nel progetto dell'utente non è disponibile una posizione predefinita in cui eseguirne l'override.

- Se possibile, personalizzare le proprietà in fase di valutazione anziché modificarle all'interno di una destinazione. In questo modo, infatti, risulterà più facile caricare un progetto e seguirne l'andamento.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Per impostazione predefinita, *Microsoft.Common.props* importa `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` e *microsoftcommon.targets* importa `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Il valore predefinito di `MSBuildProjectExtensionsPath` è `$(BaseIntermediateOutputPath)`, `obj/`. NuGet usa questo meccanismo per fare riferimento alla logica di compilazioni nei pacchetti. In fase di ripristino crea quindi file `{project}.nuget.g.props` che si riferiscono al contenuto del pacchetto.

È possibile disabilitare questo meccanismo di estendibilità impostando la proprietà `ImportProjectExtensionProps` su `false` in un file *Directory.build.props* o prima di importare *Microsoft.Common.props*.

> [!NOTE]
> Disabilitando le importazioni di MSBuildProjectExtensionsPath, la logica di compilazione nei pacchetti NuGet non sarà applicata al progetto. Per eseguire la propria funzione, alcuni pacchetti NuGet richiedono la logica di compilazione. Viene quindi eseguito il rendering se non è disabilitato.

## <a name="user-file"></a>File con estensione user

*Microsoft.Common.CurrentVersion.targets* importa `$(MSBuildProjectFullPath).user` se esiste. In questo modo è possibile creare un file accanto al progetto con tale estensione aggiuntiva. In caso di modifiche a lungo termine che saranno verificate nel controllo del codice sorgente, è preferibile modificare il progetto stesso. In questo modo i gestori futuri non dovranno necessariamente conoscere questo meccanismo di estensione.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath e MSBuildUserExtensionsPath

> [!WARNING]
> Tramite questi meccanismi di estensione è più difficile ripetere le compilazioni su più computer. Provare a usare una configurazione che può verificata nel sistema di controllo del codice sorgente e condivisa tra tutti gli sviluppatori della codebase.

Per convenzione, molti file logici di compilazione importano

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

prima del contenuto e

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

dopo. In questo modo, gli SDK installati possono espandere la logica di compilazione di tipi di progetto comuni.

La stessa struttura di directory viene ricercata in `$(MSBuildUserExtensionsPath)`, vale a dire la cartella *%LOCALAPPDATA%\Microsoft\MSBuild* per ogni utente. I file in tale cartella saranno importati per tutte le compilazioni del tipo di progetto corrispondente, eseguito con le credenziali dell'utente interessato. Per disabilitare le estensioni utente, impostare le proprietà denominate in base al file di importazione nel criterio `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Ad esempio, se `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` viene impostato su `false` l'importazione di `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` non sarà eseguita.

## <a name="customize-the-solution-build"></a>Personalizzare la compilazione della soluzione

> [!IMPORTANT]
> Questa procedura di personalizzazione della compilazione della soluzione si applica solo alle compilazioni da riga di comando con *MSBuild.exe*. **Non** si applica alle compilazioni in Visual Studio.

Quando MSBuild compila un file della soluzione, prima lo converte internamente in un file di progetto e poi lo compila. Il file di progetto generato importa `before.{solutionname}.sln.targets` prima di definire tutte le destinazioni e `after.{solutionname}.sln.targets` dopo avere importato le destinazioni, incluse le destinazioni installate nelle directory `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` e `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Ad esempio, è possibile definire una nuova destinazione per scrivere un messaggio di log personalizzato dopo la compilazione di *MyCustomizedSolution.sln* creando un file nella stessa directory denominata *after.MyCustomizedSolution.sln.targets* contenente

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>Personalizzare tutte le compilazioni .NET

Quando si gestisce un server di compilazione, potrebbe essere necessario configurare le impostazioni di MSBuild globalmente per tutte le compilazioni nel server.  In linea di principio, è possibile modificare i file Global *Microsoft. Common. targets* o *Microsoft. Common. props* , ma esiste un modo migliore. È possibile influire su tutte le compilazioni di un determinato tipo C# di progetto, ad esempio tutti i progetti, usando determinate proprietà di MSBuild e aggiungendo alcuni `.targets` personalizzati e file di `.props`.

Per influire C# su tutte le compilazioni o Visual Basic gestite da un'installazione di MSBuild o Visual Studio, creare un file *Custom. before. Microsoft. Common. targets* o *Custom. after. Microsoft. Common. targets* con destinazioni che verranno eseguite prima o dopo *Microsoft. Common. targets*oppure un file *Custom. before. Microsoft. Common* . props o *Custom. after. Microsoft.* Common. props con proprietà che verranno elaborate prima o dopo Microsoft. Common *.* Props

È possibile specificare i percorsi di questi file usando le proprietà MSBuild seguenti:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Le versioni *comuni* di queste proprietà influiscono C# sui progetti e Visual Basic. È possibile impostare queste proprietà nella riga di comando di MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

L'approccio migliore dipende dallo scenario. Se si dispone di un server di compilazione dedicato e si desidera assicurarsi che determinate destinazioni vengano sempre eseguite su tutte le compilazioni del tipo di progetto appropriato eseguite su tale server, è consigliabile utilizzare un file di `.props` o `.targets` personalizzato globale.  Se si desidera che le destinazioni personalizzate vengano eseguite solo quando si applicano determinate condizioni, utilizzare un altro percorso di file e impostare il percorso di tale file impostando la proprietà MSBuild appropriata nella riga di comando di MSBuild solo quando necessario.

> [!WARNING]
> Visual Studio USA i file di `.props` o `.targets` personalizzati se li trova nella cartella MSBuild ogni volta che compila qualsiasi progetto del tipo corrispondente. Questa operazione può avere conseguenze impreviste e, se eseguita in modo non corretto, può disabilitare la capacità di Visual Studio di essere compilata nel computer.

## <a name="customize-all-c-builds"></a>Personalizzare tutte C++ le compilazioni

Per C++ i progetti, i file di `.props` e `.targets` personalizzati indicati in precedenza vengono ignorati. Per C++ i progetti, è possibile creare file di `.targets` per ogni piattaforma e inserirli nelle cartelle di importazione appropriate per tali piattaforme.

Il file di `.targets` per la piattaforma Win32, *Microsoft. cpp. Win32. targets*, contiene l'elemento `Import` seguente:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

È presente un elemento analogo alla fine dello stesso file:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Sono presenti elementi di importazione simili per altre piattaforme di destinazione in *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {Version} \ Platforms\*.

Una volta inserito il file di `.targets` nella cartella appropriata in base alla piattaforma, MSBuild importa il file in ogni C++ compilazione per la piattaforma. Se necessario, è possibile inserire più file di `.targets`.

### <a name="specify-a-custom-import-on-the-command-line"></a>Specificare un'importazione personalizzata nella riga di comando

Per `.targets` personalizzati che si desidera includere per una compilazione specifica di un C++ progetto, impostare una o entrambe le proprietà `ForceImportBeforeCppTargets` e `ForceImportAfterCppTargets` nella riga di comando.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Per un'impostazione globale (per avere effetto su tutte le C++ compilazioni per una piattaforma in un server di compilazione), sono disponibili due metodi. In primo luogo, è possibile impostare queste proprietà usando una variabile di ambiente di sistema sempre impostata. Questa operazione funziona perché MSBuild legge sempre l'ambiente e crea o esegue l'override delle proprietà per tutte le variabili di ambiente.

## <a name="see-also"></a>Vedere anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)

- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
