---
title: Visualizzare i dati del documento e documento negli editor personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2076f1a6c96aea717470fa1e955e5b9786f7fcc5
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639815"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>I dati del documento e visualizzazione documento negli editor personalizzati
Un editor personalizzato è costituita da due parti: un oggetto dati del documento e un oggetto visualizzazione del documento. Come suggeriscono i nomi, l'oggetto dati del documento rappresenta i dati di testo da visualizzare. Analogamente, l'oggetto visualizzazione del documento (o "visualizzazione") rappresenta una o più finestre in cui visualizzare l'oggetto dati del documento.  
  
## <a name="document-data-object"></a>Oggetto dati del documento  
 Un oggetto dati del documento è una rappresentazione dei dati di testo nel buffer di testo. È un oggetto COM che consente di archiviare il testo del documento e altre informazioni. Oggetto dati del documento inoltre gestisce la persistenza di documento e Abilita più visualizzazioni dei dati. Per altre informazioni, vedere  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> e [documentare Windows](../extensibility/internals/document-windows.md).  
  
 Editor personalizzati e finestre di progettazione è possibile scegliere di usare il <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto o le proprie buffer personalizzato. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> segue il modello di incorporamento semplificato per un editor standard, supporta più visualizzazioni e fornisce interfacce eventi che vengono usate per gestire più viste.  
  
## <a name="document-view-object"></a>Oggetto visualizzazione del documento  
 Una finestra che Visualizza codice e altro testo è noto come un documento o una vista. Quando si crea un editor, è possibile scegliere una visualizzazione singola, in cui il testo viene visualizzato in una singola finestra. Oppure è possibile scegliere una visualizzazione più, in cui viene visualizzato il testo in più di una finestra. La scelta dipende dall'applicazione. Ad esempio, se è necessaria la modifica side-by-side, scelto MultipleView. Ogni visualizzazione è associata una voce in integrato dell'ambiente di sviluppo (IDE) in esecuzione (RDT) tabella del documento. Windows vista appartengono a un progetto o un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.  
  
 Se l'editor supporta più visualizzazioni di un oggetto dati del documento, quindi i dati del documento e gli oggetti di visualizzazione documento devono essere separati. In caso contrario, essi possono essere raggruppati. Per altre informazioni, vedere [supporta più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).  
  
 L'IDE notifica viste sugli eventi (ad esempio, quando una soluzione contenente un documento viene chiuso) creando una corrispondenza tra un identificatore di elemento (ID elemento) per ogni voce nella tabella documenti in esecuzione. Per altre informazioni, vedere [in esecuzione tabella document](../extensibility/internals/running-document-table.md).  
  
 Sono disponibili due opzioni per la creazione di una visualizzazione per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la visualizzazione viene inserita in una finestra tramite un controllo ActiveX o un oggetto dati del documento. Il secondo è il modello di incorporamento semplificato, in cui la vista è ospitata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> viene implementata per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [attivazione sul posto](../extensibility/in-place-activation.md). Per informazioni sul modello di incorporamento semplificato, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md)   
 [Incorporamento semplificato](../extensibility/simplified-embedding.md)   
 [Procedura: collegare visualizzazioni ai dati documento](../extensibility/how-to-attach-views-to-document-data.md)   
 [Gestione dei detentori di blocchi documento](../extensibility/document-lock-holder-management.md)   
 [Viste a schede singole e multiple](../extensibility/single-and-multi-tab-views.md)   
 [Salvare un documento standard](../extensibility/internals/saving-a-standard-document.md)   
 [Persistenza e la tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [Determinare quale editor viene aperto un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [Factory dell'editor](../extensibility/editor-factories.md)