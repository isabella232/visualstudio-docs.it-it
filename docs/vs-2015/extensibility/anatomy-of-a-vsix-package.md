---
title: Anatomia di un pacchetto VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 156b221265b4c3c23b795b09b9a50ccb27a63bcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295640"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un pacchetto VSIX è un file con estensione VSIX che contiene una o più estensioni di Visual Studio, insieme ai metadati usati da Visual Studio per classificare e installare le estensioni. I metadati sono contenuti nel manifesto VSIX e nel file [Content_Types]. XML. Un pacchetto VSIX può anche contenere uno o più file con estensione vsixlangpack per fornire il testo di installazione localizzato e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.  
  
 Il formato del pacchetto VSIX segue lo standard OPC (Open Packaging Conventions). Il pacchetto contiene i file binari e i file di supporto, insieme a un file di [Content_Types]. XML e a un file manifesto con estensione VSIX. Un pacchetto VSIX può contenere l'output di più progetti o anche più pacchetti con manifesti propri.  
  
> [!NOTE]
> I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in Uniform Resource Identifier (URI), come definito in [\[RFC2396\]](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
## <a name="the-vsix-manifest"></a>Manifesto VSIX  
 Il manifesto VSIX contiene informazioni sull'estensione da installare e segue lo schema VSX. Per altre informazioni, vedere [riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Per un esempio di manifesto VSIX, vedere [elemento PackageManifest (elemento radice, schema VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
 Il manifesto VSIX deve essere denominato `extension.vsixmanifest` quando è incluso in un file con estensione VSIX.  
  
## <a name="the-content"></a>Contenuto  
 Un pacchetto VSIX può contenere modelli, elementi della casella degli strumenti, pacchetti VSPackage o qualsiasi altro tipo di estensione supportato da Visual Studio.  
  
## <a name="language-packs"></a>Language Pack  
 Un pacchetto VSIX può contenere una o più file con estensione vsixlangpack per fornire il testo localizzato durante l'installazione. Per ulteriori informazioni, vedere la pagina relativa alla [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="dependencies-and-references"></a>Dipendenze e riferimenti  
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere il proprio manifesto VSIX.  
  
 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema utente. Se gli assembly richiesti non vengono trovati, **Extensions e Updates** Visualizza un elenco degli assembly mancanti.  
  
 Se il manifesto dell'estensione include uno o più elementi di [riferimento](https://msdn.microsoft.com/32c52934-e81e-4b53-8cb6-4df45ef7bfa8) , le **estensioni e gli aggiornamenti** confrontano il manifesto di ogni riferimento alle estensioni installate nel sistema e installano l'estensione a cui si fa riferimento, se non è già installato. Se è installata una versione precedente di un'estensione a cui si fa riferimento, la versione più recente lo sostituisce.  
  
 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento facendo clic sul riferimento per il progetto interno, quindi nella finestra **Proprietà** impostare i **gruppi di output inclusi nella proprietà VSIX** su `BuiltProjectOutputGroup`.  
  
 Per includere dll satellite da assembly a cui si fa riferimento nel pacchetto VSIX, aggiungere `SatelliteDllsProjectOutputGroup` ai **gruppi di output inclusi nella proprietà VSIX** .  
  
## <a name="installation-location"></a>Percorso di installazione  
 Durante l'installazione, le **estensioni e gli aggiornamenti** cercano il contenuto del pacchetto VSIX in una cartella in%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.  
  
 Per impostazione predefinita, l'installazione viene applicata solo all'utente corrente, perché% LocalAppData% è una directory specifica dell'utente. Tuttavia, se si imposta l'elemento [ALLUSERS](https://msdn.microsoft.com/ac817f50-3276-4ddb-b467-8bbb1432455b) del manifesto su `True`, l'estensione verrà installata in.\\*VisualStudioInstallationFolder*\Common7\IDE\Extensions e sarà disponibile per tutti gli utenti del computer.  
  
## <a name="content_typesxml"></a>[Content_Types]. XML  
 Il file [Content_Types]. XML identifica i tipi di file nel file con estensione VSIX espanso. Visual Studio usa questo file durante l'installazione del pacchetto, ma non installa il file stesso. Per ulteriori informazioni su questo file, vedere [la struttura del file Content_types\]. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
 Un file [Content_Types]. XML è richiesto dallo standard Open Packaging Conventions (OPC). Per ulteriori informazioni su OPC, vedere [OPC: un nuovo standard per](https://go.microsoft.com/fwlink/?LinkID=148207) la creazione di pacchetti di dati nel sito Web MSDN.
