---
title: Elementi di progetto MSBuild comuni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b119cae4013bd1be5657224ad54de54c10321848
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526862"
---
# <a name="common-msbuild-project-items"></a>Elementi di progetto MSBuild comuni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elementi di progetto MSBuild comuni](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-items).  
  
  
In [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], un elemento è un riferimento denominato a uno o più file. Gli elementi contengono metadati quali ad esempio nomi file, percorsi e numeri di versione. Tutti i tipi di progetto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hanno molti elementi in comune. Questi elementi sono definiti nel file microsoft.build.commontypes.xsd.  
  
## <a name="common-items"></a>Elementi comuni  
 Di seguito è riportato l'elenco di tutti gli elementi comuni dei progetti.  
  
### <a name="reference"></a>Riferimenti  
 Rappresenta un riferimento all'assembly (gestito) nel progetto.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|HintPath|Stringa facoltativa. Percorso relativo o assoluto dell'assembly.|  
|Name|Stringa facoltativa. Il nome visualizzato dell'assembly, ad esempio "System.Windows.Forms".|  
|FusionName|Stringa facoltativa. Specifica il nome Fusion semplice o sicuro per l'elemento.<br /><br /> Questo attributo, se specificato, consente di risparmiare tempo in quanto non comporta l'apertura del file di assembly per ottenere il nome Fusion.|  
|SpecificVersion|Valore booleano facoltativo. Specifica se è necessario fare riferimento solo alla versione nel nome Fusion.|  
|Alias|Stringa facoltativa. Gli alias per il riferimento.|  
|Private|Valore booleano facoltativo. Specifica se il riferimento deve essere copiato nella cartella di output. Questo attributo corrisponde alla proprietà **Copia localmente** del riferimento nell'IDE di Visual Studio.|  
  
### <a name="comreference"></a>COMReference  
 Rappresenta un riferimento a un oggetto COM (non gestito) nel progetto.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|Name|Stringa facoltativa. Nome visualizzato del componente|  
|Guid|Stringa facoltativa. GUID per il componente, nel formato {12345678-1234-1234-1234-1234567891234}.|  
|VersionMajor|Stringa facoltativa. La parte principale del numero di versione del componente. Ad esempio, "5" se il numero di versione completo è "5.46".|  
|VersionMinor|Stringa facoltativa. La parte secondaria del numero di versione del componente. Ad esempio, "46" se il numero di versione completo è "5.46."|  
|LCID|Stringa facoltativa. LocaleID per il componente.|  
|WrapperTool|Stringa facoltativa. Il nome dello strumento wrapper usato per il componente, ad esempio, "tlbimp".|  
|Isolated|Valore booleano facoltativo. Specifica se il componente è un componente reg-free.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Rappresenta un elenco di librerie dei tipi per la destinazione ResolvedComreference.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|WrapperTool|Stringa facoltativa. Il nome dello strumento wrapper usato per il componente, ad esempio, "tlbimp".|  
  
### <a name="nativereference"></a>NativeReference  
 Rappresenta un file manifesto nativo o un riferimento a tale file.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|Name|Stringa obbligatoria. Il nome base del file manifesto.|  
|HintPath|Stringa obbligatoria. Il percorso relativo del file manifesto.|  
  
### <a name="projectreference"></a>ProjectReference  
 Rappresenta un riferimento a un altro progetto.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|Name|Stringa facoltativa. Nome visualizzato del riferimento.|  
|Project|Stringa facoltativa. GUID per il riferimento, nel formato {12345678-1234-1234-1234-1234567891234}.|  
|Pacchetto|Stringa facoltativa. Il percorso del file di progetto a cui viene fatto riferimento.|  
  
### <a name="compile"></a>Compile  
 Rappresenta i file di origine per il compilatore.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|DependentUpon|Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta.|  
|AutoGen|Valore booleano facoltativo. Indica se il file è stato generato per il progetto dall'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|Collegamento|Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del file di progetto.|  
|Visible|Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1.  Never<br />2.  Sempre<br />3.  PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Rappresenta le risorse da incorporare nell'assembly generato.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|DependentUpon|Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta|  
|Generator|Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento.|  
|LastGenOutput|Stringa obbligatoria. Il nome del file che è stato creato da qualsiasi generatore di file eseguito sull'elemento.|  
|CustomToolNamespace|Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice.|  
|Link|Stringa facoltativa. Il percorso di annotazione che viene visualizzato se il file si trova fisicamente fuori dall'influenza del progetto.|  
|Visible|Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1.  Never<br />2.  Sempre<br />3.  PreserveNewest|  
|LogicalName|Stringa obbligatoria. Nome logico della risorsa incorporata.|  
  
### <a name="content"></a>Content  
 Rappresenta file che non sono compilati nel progetto, ma possono essere incorporati o pubblicati con il progetto.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|DependentUpon|Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta.|  
|Generator|Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento.|  
|LastGenOutput|Stringa obbligatoria. Il nome del file creato da qualsiasi generatore di file che è stato eseguito sull'elemento.|  
|CustomToolNamespace|Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice.|  
|Link|Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|PublishState|Stringa obbligatoria. Lo stato di pubblicazione del contenuto, che può essere:<br /><br /> - Impostazione predefinita<br />- Incluso<br />- Escluso<br />- DataFile<br />- Prerequisito|  
|IsAssembly|Valore booleano facoltativo. Specifica se il file è un assembly.|  
|Visible|Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1.  Never<br />2.  Sempre<br />3.  PreserveNewest|  
  
### <a name="none"></a>None  
 Rappresenta i file che non hanno un ruolo nel processo di compilazione.  
  
|Nome elemento|Descrizione|  
|---------------|-----------------|  
|DependentUpon|Stringa facoltativa. Specifica il file da cui questo file dipende per una compilazione corretta.|  
|Generator|Stringa obbligatoria. Il nome di un generatore di file che viene eseguito sull'elemento.|  
|LastGenOutput|Stringa obbligatoria. Il nome del file che è stato creato da qualsiasi generatore di file eseguito sull'elemento.|  
|CustomToolNamespace|Stringa obbligatoria. Lo spazio dei nomi in cui qualsiasi generatore di file eseguito su questo elemento deve creare codice.|  
|Link|Stringa facoltativa. Il percorso di annotazione che viene visualizzato quando il file si trova fisicamente fuori dall'influenza del progetto.|  
|Visible|Valore booleano facoltativo. Indica se visualizzare il file in **Esplora soluzioni** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|CopyToOutputDirectory|Stringa facoltativa. Specifica se il file deve essere copiato nella cartella di output. I valori sono:<br /><br /> 1.  Never<br />2.  Sempre<br />3.  PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Rappresenta il manifesto dell'applicazione di base per la compilazione e contiene informazioni sulla protezione di distribuzione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 Rappresenta il progetto FxCop da importare.  
  
### <a name="import"></a>Import  
 Rappresenta gli assembly i cui spazi dei nomi devono essere importati dal compilatore [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà di progetto MSBuild comuni](../msbuild/common-msbuild-project-properties.md)


