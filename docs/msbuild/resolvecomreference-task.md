---
title: Attività ResolveComReference | Microsoft Docs
description: Informazioni su MSBuild'attività ResolveComReference per ottenere un elenco di uno o più nomi di libreria dei tipi o file con estensione tlb e risolverli in percorsi su disco.
ms.custom: SEO-VS-2020
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 17e2db139df6ffd09efb43edb2cdb4e358231a1c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625578"
---
# <a name="resolvecomreference-task"></a>Attività ResolveComReference

Accetta un elenco di uno o più nomi di librerie dei tipi o file con estensione *tlb* e risolve tali librerie dei tipi in percorsi su disco.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `ResolveCOMReference` .

|Parametro|Descrizione|
|---------------|-----------------|
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la chiave pubblica viene inserita nell'assembly. Se `false`, l'assembly viene firmato completamente.|
|`EnvironmentVariables`|Parametro `String[]` facoltativo.<br /><br /> Matrice di coppie di variabili di ambiente, separate da segni di uguale. Tali variabili vengono passate ai file *tlbimp.exe* e *aximp.exe* compilati in aggiunta al blocco di ambiente regolare, oppure eseguendo l'override selettivo di tale blocco.|
|`ExecuteAsTool`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, esegue i file *tlbimp.exe* e *aximp.exe* dal framework di destinazione appropriato in modalità out-of-process per generare gli assembly wrapper necessari. Questo parametro abilita il multitargeting.|
|`IncludeVersionInInteropName`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la versione typelib sarà inclusa nel nome del wrapper. Il valore predefinito è `false`.|
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore che include una coppia di chiavi pubblica/privata.|
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica un elemento che contiene una coppia di chiavi pubblica/privata.|
|`NoClassMembers`|Parametro `Boolean` facoltativo.|
|`ResolvedAssemblyReferences`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i riferimenti all'assembly risolti.|
|`ResolvedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file con nomi completi su disco che corrispondono alle posizioni fisiche delle librerie dei tipi fornite come input per questa attività.|
|`ResolvedModules`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.|
|`SdkToolsPath`|Parametro <xref:System.String?displayProperty=fullName> facoltativo.<br /><br /> Se `ExecuteAsTool` è `true`, questo parametro deve essere impostato sul percorso degli strumenti SDK per la versione di framework di destinazione.|
|`StateFile`|Parametro `String` facoltativo.<br /><br /> Specifica il file di cache per i timestamp dei componenti COM. Se non presente, ogni esecuzione genererà nuovamente tutti i wrapper.|
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione del framework di destinazione del progetto.<br /><br /> Il valore predefinito è `String.Empty`. Tale valore indica che non viene applicato alcun filtro a un riferimento in base al framework di destinazione.|
|`TargetProcessorArchitecture`|Parametro `String` facoltativo.<br /><br /> Specifica l'architettura preferita del processore di destinazione. Viene passato al flag *tlbimp.exe*/machine dopo la conversione.<br /><br /> Il valore del parametro deve essere un membro di <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|
|`TypeLibFiles`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica il percorso del file della libreria dei tipi per i riferimenti COM. Gli elementi inclusi in questo parametro possono contenere metadati dell'elemento. Per altre informazioni, vedere la sezione [Metadati dell'elemento TypeLibFiles](#typelibfiles-item-metadata) riportata di seguito.|
|`TypeLibNames`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica i nomi delle librerie dei tipi da risolvere. Gli elementi inclusi in questo parametro devono contenere alcuni metadati dell'elemento. Per altre informazioni, vedere la sezione [Metadati dell'elemento TypeLibNames](#typelibnames-item-metadata) riportata di seguito.|
|`WrapperOutputDirectory`|Parametro `String` facoltativo.<br /><br /> Percorso su disco in cui viene inserito l'assembly di interoperabilità generato. Se questi metadati di elemento non vengono specificati, l'attività userà il percorso assoluto della directory in cui si trova il file di progetto.|

## <a name="typelibnames-item-metadata"></a>Metadati dell'elemento TypeLibNames

 Nella tabella seguente vengono descritti i metadati disponibili per gli elementi passati al parametro `TypeLibNames`.

|Metadati|Descrizione|
|--------------|-----------------|
|`GUID`|Metadati di elemento obbligatori.<br /><br /> GUID della libreria dei tipi. Se questi metadati di elemento non vengono specificati, l'attività avrà esito negativo.|
|`VersionMajor`|Metadati di elemento obbligatori.<br /><br /> Versione principale della libreria dei tipi. Se questi metadati di elemento non vengono specificati, l'attività avrà esito negativo.|
|`VersionMinor`|Metadati di elemento obbligatori.<br /><br /> Versione secondaria della libreria dei tipi. Se questi metadati di elemento non vengono specificati, l'attività avrà esito negativo.|
|`EmbedInteropTypes`|Metadati `Boolean` facoltativi.<br /><br />  Se `true`, incorporare i tipi di interoperabilità da questo riferimento direttamente nell'assembly anziché generare una DLL di interoperabilità.|
|`LocaleIdentifier`|Metadati di elemento facoltativi.<br /><br /> Identificatore delle impostazioni locali (LCID) per la libreria dei tipi. Viene specificato come valore a 32 bit che identifica la lingua preferita da un utente, un paese o un'applicazione. Se questi metadati di elemento non vengono specificati, l'attività userà l'identificatore delle impostazioni locali predefinito "0".|
|`WrapperTool`|Metadati di elemento facoltativi.<br /><br /> Specifica lo strumento wrapper usato per generare il wrapper dell'assembly per la libreria dei tipi in oggetto. Se questi metadati di elemento non vengono specificati, l'attività userà lo strumento wrapper predefinito "tlbimp". Di seguito sono riportate le opzioni disponibili per typelibs (non viene fatta distinzione tra maiuscole e minuscole):<br /><br /> -   `Primary`: usare questo strumento wrapper se si vuole usare un assembly di interoperabilità primario già generato per il componente COM. Quando si usa questo strumento wrapper, non specificare una directory di output del wrapper perché tale operazione determina l'esito negativo dell'attività.<br />-   `TLBImp`: usare questo strumento wrapper se si vuole generare un assembly di interoperabilità per il componente COM.<br />-   `AXImp`: usare questo strumento wrapper per generare un assembly di interoperabilità per un controllo ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Metadati dell'elemento TypeLibFiles

 Nella tabella seguente vengono descritti i metadati disponibili per gli elementi passati al parametro `TypeLibFiles`.

|Metadati|Descrizione|
|--------------|-----------------|
|`EmbedInteropTypes`|Parametro `Boolean` facoltativo.<br /><br />  Se `true`, incorporare i tipi di interoperabilità da questo riferimento direttamente nell'assembly anziché generare una DLL di interoperabilità.|
|`WrapperTool`|Metadati di elemento facoltativi.<br /><br /> Specifica lo strumento wrapper usato per generare il wrapper dell'assembly per la libreria dei tipi in oggetto. Se questi metadati di elemento non vengono specificati, l'attività userà lo strumento wrapper predefinito "tlbimp". Di seguito sono riportate le opzioni disponibili per typelibs (non viene fatta distinzione tra maiuscole e minuscole):<br /><br /> -   `Primary`: usare questo strumento wrapper se si vuole usare un assembly di interoperabilità primario già generato per il componente COM. Quando si usa questo strumento wrapper, non specificare una directory di output del wrapper perché tale operazione determina l'esito negativo dell'attività.<br />-   `TLBImp`: usare questo strumento wrapper se si vuole generare un assembly di interoperabilità per il componente COM.<br />-   `AXImp`: usare questo strumento wrapper per generare un assembly di interoperabilità per un controllo ActiveX.|

> [!NOTE]
> Una maggiore quantità di informazioni fornite per identificare in maniera univoca una libreria dei tipi aumenta le probabilità di risoluzione dell'attività nel file corretto su disco.

## <a name="remarks"></a>Commenti

Oltre ai parametri sopra elencati, quest'attività eredita i parametri dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base Task.](../msbuild/task-base-class.md)

Per il corretto funzionamento di questa attività, non è necessario che la DLL COM sia registrata nel computer.

## <a name="msb4803-error"></a>Errore MSB4803

Se si tenta di eseguire un progetto che usa l'attività dai comandi dell'interfaccia della riga di `ResolveCOMReference` `dotnet` comando, viene visualizzato l'errore:

```output
MSB4803: The task "ResolveComReference" is not supported on the .NET Core version of MSBuild. Please use the .NET Framework version of MSBuild.
```

Questa attività non è supportata nella versione .NET Core di MSBuild, che è ciò che viene usato quando si esegue il comando `dotnet build` dalla riga di comando. Provare a compilare il [progetto richiamandoMSBuild.exe](msbuild-command-line-reference.md) dal Visual Studio Prompt dei comandi per gli sviluppatori, perché usa la .NET Framework di MSBuild.

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
