---
title: Personalizzare la compilazione | Microsoft Docs
description: Informazioni su diversi hook di estendibilità che è possibile usare per personalizzare MSBuild progetti che usano il processo di compilazione standard.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 89ea3e2b08507e2bf6724f12951e0a35d76dfd08
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980688"
---
# <a name="customize-your-build"></a>Personalizzare la compilazione

I progetti MSBuild che usano il processo di compilazione standard, vale a dire l'importazione di *Microsoft.Common.props* e *Microsoft.Common.targets*, possono usare diversi hook di estensibilità per personalizzare il processo di compilazione.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Aggiungere argomenti alle chiamate di MSBuild da riga di comando per il progetto

Il file *Directory.Build.rsp* contenuto nella directory di origine o in una directory superiore viene applicato alle compilazioni da riga di comando del progetto. Per informazioni dettagliate, vedere [File di risposta MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props e Directory.Build.targets

Nelle versioni di MS Build precedenti alla 15, per specificare una nuova proprietà personalizzata per i progetti nella soluzione, è necessario aggiungere manualmente un riferimento a tale proprietà per ogni file di progetto della soluzione. In caso contrario, è necessario definire la proprietà in un file *props* e quindi importare in modo esplicito il file *props* in ogni progetto della soluzione, tra le altre cose.

Ora è tuttavia possibile aggiungere una nuova proprietà a ogni progetto in un unico passaggio, definendola in un singolo file denominato *Directory.Build.props* nella cartella radice che contiene l'origine. Quando MSBuild, *Microsoft.Common.props* cerca nella struttura di directory il file *Directory.Build.props* (e *Microsoft.Common.targets* cerca *Directory.Build.targets*). Se trova la struttura, importa la proprietà. *Directory.Build.props* è un file definito dall'utente che fornisce personalizzazioni ai progetti in una directory.

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

Le proprietà impostate in *Directory.Build.props* possono essere sostituite altrove nel file di progetto o nei file importati, pertanto è consigliabile pensare alle impostazioni in *Directory.Build.props* come a specificare le impostazioni predefinite per i progetti.

*Directory.Build.targets viene* importato da *Microsoft.Common.targets* dopo l'importazione di *file con* estensione targets NuGet pacchetti. Può quindi eseguire l'override delle proprietà e delle destinazioni definite nella maggior parte della logica di compilazione o impostare le proprietà per tutti i progetti indipendentemente da ciò che i singoli progetti impostano.

Quando è necessario impostare una proprietà o definire una destinazione per un singolo progetto che esegue l'override di qualsiasi impostazione precedente, inserire tale logica nel file di progetto dopo l'importazione finale. Per eseguire questa operazione in un progetto di tipo SDK, è prima necessario sostituire l'attributo di tipo SDK con le importazioni equivalenti. Vedere [How to use MSBuild project SDK (Come usare](how-to-use-project-sdk.md)MSBuild SDK del progetto).

> [!NOTE]
> Il motore MSBuild legge tutti i file importati durante la valutazione, prima di avviare l'esecuzione della compilazione per qualsiasi progetto (inclusi gli eventuali ), quindi questi file non devono essere modificati da o da qualsiasi altra parte del processo di `PreBuildEvent` `PreBuildEvent` compilazione. Le modifiche non vengono applicate fino alla chiamata successiva di *MSBuild.exe* o alla successiva Visual Studio compilazione.

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

Potrebbe essere preferibile usare proprietà comuni per tutti i progetti *(1)*, proprietà comuni per i progetti *src**(2-src)* e proprietà comuni per i progetti *test**(2-test)*.

Per consentire a MSBuild di unire correttamente i file "interni"(*2-src* e *2-test*) e il file "esterno" (*1*), è necessario tenere presente che quando MSBuild trova un file *Directory.Build.props*, interrompe l'analisi. Per continuare l'analisi e completare l'unione con il file esterno, inserire questo codice in entrambi i file interni:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

L'approccio generale di MSBuild può essere riepilogato come segue:

- Per ogni progetto, MSBuild trova il primo file *Directory.Build.props* procedendo verso l'alto nella struttura della soluzione, lo unisce ai valori predefiniti e interrompe l'analisi
- Se si desidera che più livelli siano trovati e uniti, (come illustrato sopra) il [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) file "esterno" dal file "interno"
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
> Questa procedura di personalizzazione della compilazione della soluzione si applica solo alle compilazioni da riga di comando con *MSBuild.exe*. **Non** si applica alle compilazioni in Visual Studio. Per questo motivo, non è consigliabile inserire la personalizzazione a livello di soluzione. Un'alternativa migliore per la personalizzazione di tutti i progetti in una soluzione consiste nell'usare i file *Directory.Build.props* e *Directory.build.targets* nella cartella della soluzione, come descritto altrove in questo articolo.

Quando MSBuild compila un file della soluzione, prima lo converte internamente in un file di progetto e poi lo compila. Il file di progetto generato importa `before.{solutionname}.sln.targets` prima di definire tutte le destinazioni e `after.{solutionname}.sln.targets` dopo avere importato le destinazioni, incluse le destinazioni installate nelle directory `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` e `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Ad esempio, è possibile definire una nuova destinazione per scrivere un messaggio di log personalizzato dopo la compilazione di *MyCustomizedSolution.sln* creando un file nella stessa directory denominata *after.MyCustomizedSolution.sln.targets* contenente

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

La compilazione della soluzione è separata dalle compilazioni del progetto, quindi le impostazioni qui non influiscono sulle compilazioni del progetto.

## <a name="customize-all-net-builds"></a>Personalizzare tutte le build .NET

Quando si mantiene un server di compilazione, potrebbe essere necessario configurare MSBuild a livello globale per tutte le compilazioni nel server.  In linea di principio, è possibile modificare i file *Microsoft.Common.Targets* o *Microsoft.Common.Props* globali, ma esiste un modo migliore. È possibile influire su tutte le compilazioni di un determinato tipo di progetto,ad esempio tutti i progetti C#, usando determinate proprietà MSBuild e aggiungendo determinati file `.targets` e `.props` personalizzati.

Per influire su tutte le compilazioni C# o Visual Basic regolate da un'installazione di MSBuild o Visual Studio, creare un file *Custom.Before.Microsoft.Common.Targets* o *Custom.After.Microsoft.Common.Targets* con destinazioni che verranno eseguite prima o dopo *Microsoft.Common.targets* oppure un file *Custom.Before.Microsoft.Common.Props* o *Custom.After.Microsoft.Common.Props* con proprietà che verranno elaborate prima o dopo *Microsoft.Common.props*.

È possibile specificare i percorsi di questi file usando le proprietà MSBuild seguenti:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Le *versioni* comuni di queste proprietà influiscono sui progetti Visual Basic C#. È possibile impostare queste proprietà nella riga MSBuild comando.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

L'approccio migliore dipende dallo scenario. Usando Visual Studio estendibilità, è possibile personalizzare il sistema di compilazione e fornire un meccanismo per l'installazione e la gestione delle personalizzazioni.

Se si dispone di un server di compilazione dedicato e si vuole assicurarsi che determinate destinazioni siano sempre eseguite su tutte le compilazioni del tipo di progetto appropriato che vengono eseguite in tale server, è opportuno usare un file personalizzato o `.targets` `.props` globale.  Se si desidera che le destinazioni personalizzate vengono eseguite solo quando si applicano determinate condizioni, usare un altro percorso di file e impostare il percorso di tale file impostando la proprietà MSBuild appropriata nella riga di comando di MSBuild solo quando necessario.

> [!WARNING]
> Visual Studio usa i file personalizzati o se li trova nella cartella MSBuild ogni volta che compila un progetto `.targets` `.props` del tipo corrispondente. Questa operazione può avere conseguenze impreviste e, se eseguita in modo non corretto, può disabilitare la Visual Studio di compilazione nel computer.

## <a name="customize-c-builds"></a>Personalizzare le compilazioni C++

Per i progetti C++, i file con estensione *targets* e *props* personalizzati menzionati in precedenza non possono essere usati nello stesso modo per eseguire l'override delle impostazioni predefinite. *Directory.Build.props* viene importato da *Microsoft.Common.props*, che viene importato in mentre la maggior parte delle impostazioni predefinite è definita `Microsoft.Cpp.Default.props` in *Microsoft.Cpp.props* e per diverse proprietà non è possibile usare una condizione "se non ancora definita", perché la proprietà è già definita, ma il valore predefinito deve essere diverso per determinate proprietà del progetto definite in (vedere la struttura di file con estensione `PropertyGroup` `Label="Configuration"` [vcxproj](/cpp/build/reference/vcxproj-file-structure)e props ).

È tuttavia possibile usare le proprietà seguenti per specificare i file con estensione *props* da importare automaticamente prima o dopo i file *\* Microsoft.Cpp:*

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Per personalizzare i valori predefiniti delle proprietà per tutte le compilazioni C++, creare un altro file *props* (ad *esempio, MyProps.props)* e definire la proprietà in modo che punti a tale `ForceImportAfterCppProps` `Directory.Build.props` file:

```xml
<PropertyGroup>
  <ForceImportAfterCppProps>$(MsbuildThisFileDirectory)\MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>
```

*MyProps.props* verrà importato automaticamente alla fine di *Microsoft.Cpp.props*.

## <a name="customize-all-c-builds"></a>Personalizzare tutte le compilazioni C++

La personalizzazione dell'installazione di Visual Studio non è consigliata, perché non è facile tenere traccia di tali personalizzazioni, ma se si estende Visual Studio per personalizzare le compilazioni C++ per una determinata piattaforma, è possibile creare file per ogni piattaforma e posizionarli nelle cartelle di importazione appropriate per tali piattaforme come parte di `.targets` un'estensione Visual Studio.

Il `.targets` file per la piattaforma Win32, *Microsoft.Cpp.Win32.targets,* contiene l'elemento `Import` seguente:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

È presente un elemento simile alla fine dello stesso file:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Elementi di importazione simili esistono per altre piattaforme di destinazione in *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms \* .

Dopo aver inserito il file nella cartella appropriata in base alla piattaforma, MSBuild importa il file in ogni build `.targets` `ImportAfter` C++ per tale piattaforma. È possibile inserire più `.targets` file, se necessario. 

Usando Visual Studio estendibilità, sono possibili altre personalizzazioni, ad esempio la definizione di una nuova piattaforma. Per altre informazioni, vedere [Estendibilità del progetto C++.](../extensibility/visual-cpp-project-extensibility.md)

### <a name="specify-a-custom-import-on-the-command-line"></a>Specificare un'importazione personalizzata nella riga di comando

Per informazioni personalizzate da includere per una build specifica di un progetto C++, impostare una o entrambe le proprietà `.targets` e nella riga di `ForceImportBeforeCppTargets` `ForceImportAfterCppTargets` comando.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Per un'impostazione globale (per influire, ad esempio, su tutte le compilazioni C++, per una piattaforma in un server di compilazione), sono disponibili due metodi. In primo luogo, è possibile impostare queste proprietà usando una variabile di ambiente di sistema sempre impostata. Ciò funziona perché MSBuild legge sempre l'ambiente e crea (o esegue l'override) le proprietà per tutte le variabili di ambiente.

## <a name="see-also"></a>Vedi anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
