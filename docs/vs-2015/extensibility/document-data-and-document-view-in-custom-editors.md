---
title: Visualizzazione dei dati e dei documenti negli editor personalizzati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f73ffde43f2ef3608ae492a9643f7920243d818
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204678"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dati documento e visualizzazione documento negli editor personalizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un editor personalizzato è costituito da due parti: un oggetto dati del documento e un oggetto visualizzazione del documento. Come suggerisce il nome, l'oggetto dati del documento rappresenta i dati di testo da visualizzare e l'oggetto visualizzazione documento (o "visualizzazione") rappresenta una o più finestre in cui visualizzare l'oggetto dati del documento.  
  
## <a name="document-data-object"></a>Oggetto dati documento  
 Un oggetto dati del documento è una rappresentazione di dati del testo nel buffer di testo. Si tratta di un oggetto COM che archivia testo del documento e altre informazioni, gestisce la persistenza del documento e Abilita più visualizzazioni dei dati. Per ulteriori informazioni, vedere  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> e [finestre del documento](../extensibility/internals/document-windows.md).  
  
 Gli editor e le finestre di progettazione personalizzati possono scegliere di utilizzare l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto o il relativo buffer personalizzato. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> segue il modello di incorporamento semplificato per un editor standard, supporta più visualizzazioni e fornisce le interfacce eventi usate per gestire più visualizzazioni.  
  
## <a name="document-view-object"></a>Oggetto visualizzazione documento  
 Una finestra che Visualizza codice e altro testo è nota come visualizzazione o visualizzazione del documento. Quando si crea un editor, è possibile scegliere una singola visualizzazione, in cui il testo viene visualizzato in una singola finestra o in una visualizzazione multipla, in cui il testo viene visualizzato in più di una finestra. La scelta dipende dall'applicazione. Se ad esempio è necessario modificare side-by-Side, scegliere visualizzazione multipla. Ogni visualizzazione è associata a una voce Integrated Development Environment nella tabella documenti (IDE) in esecuzione (RDT). Le finestre di visualizzazione appartengono a un progetto o a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.  
  
 Se l'editor supporta più visualizzazioni di un oggetto dati del documento, gli oggetti dati del documento e visualizzazione documento devono essere distinti. In caso contrario, è possibile raggrupparli insieme. Per altre informazioni, vedere [supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).  
  
 L'IDE notifica le visualizzazioni sugli eventi (ad esempio, quando una soluzione contenente un documento viene chiusa) associando un identificatore di elemento (ItemID) per ogni voce nella tabella documenti in esecuzione. Per altre informazioni, vedere esecuzione della [tabella documenti](../extensibility/internals/running-document-table.md).  
  
 Sono disponibili due opzioni per la creazione di una vista per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la vista è ospitata in una finestra utilizzando un controllo ActiveX o un oggetto dati del documento. Il secondo è il modello di incorporamento semplificato, in cui la vista è ospitata da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ed <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> è implementata per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [attivazione sul posto](../misc/in-place-activation.md). Per informazioni sul modello di incorporamento semplificato, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di più visualizzazioni di documenti](../extensibility/supporting-multiple-document-views.md)   
 [Incorporamento semplificato](../extensibility/simplified-embedding.md)   
 [Procedura: aggiungere visualizzazioni ai dati del documento](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestione dei contenitori di blocco del documento](../extensibility/document-lock-holder-management.md)   
 [Visualizzazioni singole e a più schede](../extensibility/single-and-multi-tab-views.md)   
 [Salvataggio di un documento standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenza e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinazione dell'editor che apre un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Factory editor](../extensibility/editor-factories.md)
