---
title: Riferimenti delle attività MSBuild | Microsoft Docs
description: Informazioni sulle attività incluse in MSBuild, che forniscono il codice eseguito durante il processo di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5f6d8c4d7907da705de8f204f93c007c13b2e67749f3bc089fc48ee674909a8b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397514"
---
# <a name="msbuild-task-reference"></a>Riferimenti delle attività MSBuild

Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Le attività nell'elenco seguente sono incluse in MSBuild. Quando viene installato il carico di lavoro C++, sono disponibili attività aggiuntive che vengono usate per compilare progetti C++. Per altre informazioni, vedere [Attività C++.](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)

Oltre ai parametri elencati negli argomenti di questa sezione, ogni attività dispone anche dei parametri seguenti:

| Parametro | Descrizione |
|-------------------| - |
| `Condition` | Parametro `String` facoltativo.<br /><br /> Espressione `Boolean` utilizzata dal motore MSBuild per determinare se questa attività verrà eseguita. Per informazioni sulle condizioni supportate da MSBuild, vedere [Condizioni](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parametro facoltativo. Può contenere uno dei valori seguenti:<br /><br /> -   **WarnAndContinue** o **true.** Quando un'attività ha esito negativo, le attività successive [nell'elemento Target](../msbuild/target-element-msbuild.md) e nella compilazione continuano a essere eseguite e tutti gli errori dell'attività vengono considerati avvisi.<br />-   **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.<br />-   **ErrorAndStop o** **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.<br /><br /> Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.<br /><br /> Per altre informazioni, vedere [Procedura: Ignorare gli errori nelle attività](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Contenuto della sezione

- [Classe di base Task](../msbuild/task-base-class.md)

 Aggiunge diversi parametri alle attività che derivano dalla classe <xref:Microsoft.Build.Utilities.Task>. Non deve essere usato direttamente.

- [Classe di base TaskExtension](../msbuild/taskextension-base-class.md)

 Aggiunge diversi parametri alle attività che derivano dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>. Non deve essere usato direttamente.

- [Classe di base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Aggiunge diversi parametri alle attività che derivano dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Non deve essere usato direttamente.

- [Attività AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)

 Crea un assembly con un manifesto da uno o più file che costituiscono moduli o file di risorse.

- [AspNetCompiler (attività)](../msbuild/aspnetcompiler-task.md)

 Esegue il *wrappingaspnet_compiler.exe*, un'utilità per precompilare ASP.NET applicazioni.

- [AssignCulture (attività)](../msbuild/assignculture-task.md)

 Assegna gli identificatori delle impostazioni cultura agli elementi.

- [Attività AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)

 Accetta un elenco di stringhe di configurazione e li assegna ai progetti specificati.

- [Attività AssignTargetPath](../msbuild/assigntargetpath-task.md)

 Accetta un elenco di file e aggiunge gli attributi `<TargetPath>`, se non sono già specificati.

- [attività CallTarget](../msbuild/calltarget-task.md)

 Richiama una destinazione nel file di progetto.

- [attività CombinePath](../msbuild/combinepath-task.md)

 Combina i percorsi specificati in un singolo percorso.

- [attività ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)

 Converte un percorso relativo, o un riferimento, in un percorso assoluto.

- [Copy (attività)](../msbuild/copy-task.md)

 Copia i file in una nuova posizione.

- [attività CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)

 Crea un nome di manifesto di tipo C# da un nome di file con estensione *resx* specificato o da un'altra risorsa.

- [CreateItem (attività)](../msbuild/createitem-task.md)

 Popola le raccolte di elementi dagli elementi di input, consentendo la copia degli elementi da un elenco a un altro.

- [CreateProperty (attività)](../msbuild/createproperty-task.md)

 Popola le proprietà dai valori di input, consentendo la copia di tali valori da una proprietà o una stringa a un'altra.

- [Crea attività VisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Crea un Visual Basic di manifesto in stile predefinito da un nome di file con estensione *resx* specificato o da un'altra risorsa.

- [Csc (attività)](../msbuild/csc-task.md)

 Richiama il compilatore Visual C# per creare librerie eseguibili a collegamento dinamico o moduli di codice.

- [Delete (attività)](../msbuild/delete-task.md)

 Elimina i file specificati.

- [Attività DownloadFile](../msbuild/downloadfile-task.md)

 Scarica un file nella posizione specificata.

- [attività Error](../msbuild/error-task.md)

 Interrompe una compilazione e registra un errore in base a un'istruzione condizionale valutata.

- [Exec (attività)](../msbuild/exec-task.md)

 Esegue il programma o il comando specificato con gli argomenti specificati.

- [FindAppConfigFile (attività)](../msbuild/findappconfigfile-task.md)

 Trova il *app.config* file, se presente, negli elenchi forniti.

- [FindInList (attività)](../msbuild/findinlist-task.md)

 Trova un elemento in un elenco specificato con un itemspec corrispondente.

- [FindUnderPath (attività)](../msbuild/findunderpath-task.md)

 Determina gli elementi di una raccolta specificata presenti nella cartella indicata e in tutte le relative sottocartelle.

- [FormatUrl task (attività)](../msbuild/formaturl-task.md)

 Converte un URL in un formato URL corretto.

- [Attività FormatVersion](../msbuild/formatversion-task.md)

 Aggiunge il numero di revisione al numero di versione.

- [GenerateApplicationManifest (attività)](../msbuild/generateapplicationmanifest-task.md)

 Genera un manifesto ClickOnce'applicazione o un manifesto nativo.

- [GenerateBootstrapper (attività)](../msbuild/generatebootstrapper-task.md)

 Consente di rilevare, scaricare e installare automaticamente un'applicazione e i relativi prerequisiti.

- [GenerateDeploymentManifest (attività)](../msbuild/generatedeploymentmanifest-task.md)

 Genera un manifesto ClickOnce distribuzione.

- [GenerateResource (attività)](../msbuild/generateresource-task.md)

 Converte *.txt* file con estensione *resx in* file con estensione resources binari *di* Common Language Runtime.

- [GenerateTrustInfo (attività)](../msbuild/generatetrustinfo-task.md)

 Genera l'attendibilità dell'applicazione dal manifesto di base e dai parametri `TargetZone` e `ExcludedPermissions`.

- [GetAssemblyIdentity (attività)](../msbuild/getassemblyidentity-task.md)

 Recupera le identità degli assembly dai file specificati ed estrae le informazioni sulle identità.

- [Attività GetFileHash](../msbuild/getfilehash-task.md)

 Calcola i checksum del contenuto di un file o di un set di file.

- [GetFrameworkPath (attività)](../msbuild/getframeworkpath-task.md)

 Recupera il percorso degli assembly di .NET Framework.

- [GetFrameworkSdkPath (attività)](../msbuild/getframeworksdkpath-task.md)

 Recupera il percorso del Windows Software Development Kit (SDK).

- [Attività GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)

 Restituisce i percorsi degli assembly di riferimento dei vari framework.

- [LC (attività)](../msbuild/lc-task.md)

 Genera un file *con estensione license* da un file con estensione *licx.*

- [MakeDir (attività)](../msbuild/makedir-task.md)

 Crea directory e, se necessario, eventuali directory padre.

- [attività Message](../msbuild/message-task.md)

 Registra un messaggio durante una compilazione.

- [Move (attività)](../msbuild/move-task.md)

 Sposta i file in una nuova posizione.

- [MSBuild (attività)](../msbuild/msbuild-task.md)

 Compila MSBuild progetti da un altro MSBuild progetto.

- [ReadLinesFromFile (attività)](../msbuild/readlinesfromfile-task.md)

 Legge un elenco di elementi da un file di testo.

- [RegisterAssembly (attività)](../msbuild/registerassembly-task.md)

 Legge i metadati nell'assembly specificato e aggiunge le voci necessarie nel Registro di sistema.

- [RemoveDir (attività)](../msbuild/removedir-task.md)

 Rimuove le directory specificate con tutti i relativi file e sottodirectory.

- [RemoveDuplicates (attività)](../msbuild/removeduplicates-task.md)

 Rimuove gli elementi duplicati dalla raccolta di elementi specificata.

- [RequiresFramework35SP1Assembly (attività)](../msbuild/requiresframework35sp1assembly-task.md)

 Determina se l'applicazione richiede .NET Framework 3.5 SP1.

- Attività ResGen

 Obsoleta. Usare [l'attività GenerateResource](../msbuild/generateresource-task.md) per convertire *.txt* file *resx* in e da file con estensione resources binari *di* Common Language Runtime.

- [ResolveAssemblyReference (attività)](../msbuild/resolveassemblyreference-task.md)

 Determina tutti gli assembly che dipendono dall'assembly specificato.

- [Attività ResolveComReference](../msbuild/resolvecomreference-task.md)

 Accetta un elenco di uno o più nomi di librerie dei tipi o file con estensione *tlb* e risolve tali librerie dei tipi in percorsi su disco.

- [ResolveKeySource (attività)](../msbuild/resolvekeysource-task.md)

 Determina l'origine delle chiavi con nome sicuro.

- [ResolveManifestFiles (attività)](../msbuild/resolvemanifestfiles-task.md)

 Risolve gli elementi seguenti del processo di compilazione nei file per la generazione del manifesto: elementi compilati, dipendenze, satelliti, contenuto, simboli di debug e documentazione.

- [ResolveNativeReference (attività)](../msbuild/resolvenativereference-task.md)

 Risolve i riferimenti nativi.

- [ResolveNonMSBuildProjectOutput (attività)](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Determina i file di output per riferimenti a progetti non MSBuild.

- [SGen (attività)](../msbuild/sgen-task.md)

 Crea un assembly di serializzazione XML per i tipi presenti nell'assembly specificato.

- [SignFile (attività)](../msbuild/signfile-task.md)

 Consente di firmare il file specificato usando il certificato specificato.

- [Touch (attività)](../msbuild/touch-task.md)

 Imposta l'ora di accesso e di modifica dei file.

- [UnregisterAssembly (attività)](../msbuild/unregisterassembly-task.md)

 Annulla la registrazione degli assembly specificati ai fini dell'interoperabilità COM.

- [Attività Unzip](../msbuild/unzip-task.md)

 Decomprime un archivio con estensione *zip* nella posizione specificata.

- [Attività UpdateManifest](../msbuild/updatemanifest-task.md)

 Aggiorna le proprietà selezionate in un manifesto e ripete la firma.

- [Vbc (attività)](../msbuild/vbc-task.md)

 Richiama il compilatore Basic per creare librerie eseguibili a collegamento dinamico o moduli di codice.

- [Attività VerifyFileHash](../msbuild/verifyfilehash-task.md)

 Verifica che un file corrisponda all'hash file previsto.

- [attività Warning](../msbuild/warning-task.md)

 Registra un avviso durante una compilazione in base a un'istruzione condizionale valutata.

- [Attività WriteCodeFragment](../msbuild/writecodefragment-task.md)

 Genera un file di codice temporaneo tramite il frammento di codice generato specificato. Non elimina il file.

- [WriteLinesToFile (attività)](../msbuild/writelinestofile-task.md)

 Scrive gli elementi specificati nel file di testo indicato.

- [Attività XmlPeek](../msbuild/xmlpeek-task.md)

 Restituisce valori come specificato dalla query XPath da un file XML.

- [XmlPoke (attività)](../msbuild/xmlpoke-task.md)

 Imposta i valori come specificato da una query XPath in un file XML.

- [XslTransformation (attività)](../msbuild/xsltransformation-task.md)

 Trasforma un input XML tramite *Extensible Stylesheet Language Transformation* (XSLT) o un XSLT compilato e gli output in un dispositivo o file di output.

- [Attività ZipDirectory](../msbuild/zipdirectory-task.md)

 Crea un archivio con estensione *zip* dal contenuto di una directory.

## <a name="see-also"></a>Vedi anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Scrittura di attività](../msbuild/task-writing.md)
- [Attività](../msbuild/msbuild-tasks.md)
