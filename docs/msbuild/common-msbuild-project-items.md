---
title: Elementi di progetto MSBuild comuni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb759ba9571e16d0030f1fd6baf6d4feb03efb2e
ms.sourcegitcommit: 510529f2f86a9897ed5767973e60c99c0d3a77a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73956141"
---
# <a name="common-msbuild-project-items"></a>Elementi di progetto MSBuild comuni
In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], un elemento è un riferimento denominato a uno o più file. Gli elementi contengono metadati quali ad esempio nomi file, percorsi e numeri di versione. Tutti i tipi di progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hanno molti elementi in comune. Questi elementi sono definiti nel file *Microsoft.Build.CommonTypes.xsd*.

## <a name="common-items"></a>Elementi comuni
 Di seguito è riportato l'elenco di tutti gli elementi comuni dei progetti.

### <a name="reference"></a>Reference
 Rappresenta un riferimento all'assembly (gestito) nel progetto.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|HintPath|Stringa facoltativa. Percorso relativo o assoluto dell'assembly.|
|Name|Stringa facoltativa. Il nome visualizzato dell'assembly, ad esempio "System.Windows.Forms".|
|FusionName|Stringa facoltativa. Specifica il nome Fusion semplice o sicuro per l'elemento.<br /><br /> Questo attributo, se specificato, consente di risparmiare tempo in quanto non comporta l'apertura del file di assembly per ottenere il nome Fusion.|
|SpecificVersion|Valore booleano facoltativo. Specifica se è necessario fare riferimento solo alla versione nel nome Fusion.|
|Alias|Stringa facoltativa. Gli alias per il riferimento.|
|Private|Valore booleano facoltativo. Specifica se il riferimento deve essere copiato nella cartella di output. Questo attributo corrisponde alla proprietà **Copia localmente** del riferimento nell'IDE di Visual Studio.|

### <a name="comreference"></a>COMReference
 Rappresenta un riferimento a un oggetto COM (non gestito) nel progetto. Questo elemento si applica solo ai progetti .NET.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|Name|Stringa facoltativa. Nome visualizzato del componente|
|GUID|Stringa obbligatoria. GUID per il componente, nel formato {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Stringa obbligatoria. La parte principale del numero di versione del componente. Ad esempio, "5" se il numero di versione completo è "5.46".|
|VersionMinor|Stringa obbligatoria. La parte secondaria del numero di versione del componente. Ad esempio, "46" se il numero di versione completo è "5.46."|
|LCID|Stringa facoltativa. LocaleID per il componente.|
|WrapperTool|Stringa facoltativa. Il nome dello strumento wrapper usato per il componente, ad esempio, "tlbimp".|
|Isolated|Valore booleano facoltativo. Specifica se il componente è un componente reg-free.|

### <a name="comfilereference"></a>COMFileReference
 Rappresenta un elenco di librerie di tipi passate al parametro `TypeLibFiles` della destinazione [ResolvedComreference](resolvecomreference-task.md). Questo elemento si applica solo ai progetti .NET.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|WrapperTool|Stringa facoltativa. Il nome dello strumento wrapper usato per il componente, ad esempio, "tlbimp".|

### <a name="nativereference"></a>NativeReference
 Rappresenta un file manifesto nativo o un riferimento a tale file.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|Name|Stringa obbligatoria. Il nome base del file manifesto.|
|HintPath|Stringa obbligatoria. Il percorso relativo del file manifesto.|

### <a name="projectreference"></a>ProjectReference
 Rappresenta un riferimento a un altro progetto.

|Nome metadati degli elementi|Descrizione|
|---------------|-----------------|
|Name|Stringa facoltativa. Nome visualizzato del riferimento.|
|Progetto|Stringa facoltativa. GUID per il riferimento, nel formato {12345678-1234-1234-1234-1234567891234}.|
|Pacchetto|Stringa facoltativa. Il percorso del file di progetto a cui viene fatto riferimento.|
|ReferenceOutputAssembly|Valore booleano facoltativo. Se impostato su `false`, non include l'output del progetto a cui si fa riferimento come [riferimento](#reference) del progetto, ma assicura che l'altro progetto venga compilato prima di questo. Il valore predefinito è `true`.|

### <a name="compile"></a>Compile
 Rappresenta i file di origine per il compilatore.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta. |
| AutoGen | Valore booleano facoltativo. Indica se il file è stato generato per il progetto dall'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del file di progetto. |
| Visibile | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource
 Rappresenta le risorse da incorporare nell'assembly generato.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta |
| Generator | Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento. |
| LastGenOutput | Stringa obbligatoria. Il nome del file che è stato creato da qualsiasi generatore di file eseguito sull'elemento. |
| CustomToolNamespace | Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato se il file si trova fisicamente fuori dall'influenza del progetto. |
| Visibile | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |
| LogicalName | Stringa obbligatoria. Nome logico della risorsa incorporata. |

### <a name="content"></a>Contenuto
 Rappresenta file che non sono compilati nel progetto, ma possono essere incorporati o pubblicati con il progetto.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta. |
| Generator | Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento. |
| LastGenOutput | Stringa obbligatoria. Il nome del file creato da qualsiasi generatore di file che è stato eseguito sull'elemento. |
| CustomToolNamespace | Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del progetto. |
| PublishState | Stringa obbligatoria. Lo stato di pubblicazione del contenuto, che può essere:<br /><br /> - Impostazione predefinita<br />- Incluso<br />- Escluso<br />- DataFile<br />- Prerequisito |
| IsAssembly | Valore booleano facoltativo. Specifica se il file è un assembly. |
| Visibile | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |

### <a name="none"></a>Nessuno
 Rappresenta i file che non hanno un ruolo nel processo di compilazione.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| DependentUpon | Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta. |
| Generator | Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento. |
| LastGenOutput | Stringa obbligatoria. Il nome del file che è stato creato da qualsiasi generatore di file eseguito sull'elemento. |
| CustomToolNamespace | Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice. |
| Collegamento | Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del progetto. |
| Visibile | Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1. mai<br />2. always<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata
 Rappresenta gli attributi di assembly da generare come `[AssemblyMetadata(key, value)]`.

| Nome metadati degli elementi | Descrizione |
|-----------------------| - |
| Includi | Diventa il primo parametro (chiave) nel costruttore dell'attributo `AssemblyMetadataAttribute`. |
| Value | Stringa obbligatoria. Diventa il secondo parametro (valore) nel costruttore dell'attributo `AssemblyMetadataAttribute`. |

> [!NOTE]
> Questo vale per i progetti che usano solo la .NET Core SDK.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest
 Rappresenta il manifesto dell'applicazione di base per la compilazione e contiene informazioni sulla protezione di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

### <a name="codeanalysisimport"></a>CodeAnalysisImport
 Rappresenta il progetto FxCop da importare.

### <a name="import"></a>Import
 Rappresenta gli assembly i cui spazi dei nomi devono essere importati dal compilatore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Vedere anche
- [Proprietà di progetto MSBuild comuni](../msbuild/common-msbuild-project-properties.md)
