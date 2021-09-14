---
title: Dati del documento e visualizzazione documento negli editor personalizzati | Microsoft Docs
description: Informazioni sui componenti di un editor personalizzato, ovvero l'oggetto dati del documento e l'oggetto visualizzazione documento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5cee92e4831b1639293064f6776430359eebefb0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711799"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dati del documento e visualizzazione del documento negli editor personalizzati
Un editor personalizzato è costituito da due parti: un oggetto dati del documento e un oggetto visualizzazione documento. Come suggerisce i nomi, l'oggetto dati del documento rappresenta i dati di testo da visualizzare. Analogamente, l'oggetto visualizzazione documento (o "visualizzazione") rappresenta una o più finestre in cui visualizzare l'oggetto dati del documento.

## <a name="document-data-object"></a>Oggetto dati del documento
 Un oggetto dati del documento è una rappresentazione dei dati del testo nel buffer di testo. Si tratta di un oggetto COM che archivia il testo del documento e altre informazioni. L'oggetto dati del documento gestisce anche la persistenza del documento e abilita più visualizzazioni dei relativi dati. Per ulteriori informazioni, vedere

 <xref:EnvDTE80.Window2.DocumentData%2A>e [Document Windows](../extensibility/internals/document-windows.md).

 Gli editor e le finestre di progettazione personalizzati possono scegliere di usare <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> l'oggetto o il proprio buffer personalizzato. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> segue il modello di incorporamento semplificato per un editor standard, supporta più visualizzazioni e fornisce interfacce eventi usate per gestire più visualizzazioni.

## <a name="document-view-object"></a>Oggetto visualizzazione documento
 Una finestra che visualizza codice e altro testo è nota come visualizzazione o visualizzazione documento. Quando si crea un editor, è possibile scegliere una singola visualizzazione, in cui il testo viene visualizzato in una singola finestra. In caso contrario, è possibile scegliere una visualizzazione multipla, in cui il testo viene visualizzato in più finestre. La scelta dipende dall'applicazione. Ad esempio, se è necessaria la modifica side-by-side, è necessario scegliere più visualizzazione. Ogni vista è associata a una voce nell'IDE (Integrated Development Environment) che esegue la tabella di documenti (RDT). Le finestre di visualizzazione appartengono a un progetto o a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.

 Se l'editor supporta più visualizzazioni di un oggetto dati del documento, i dati del documento e gli oggetti visualizzazione documento devono essere separati. In caso contrario, possono essere raggruppati. Per altre informazioni, vedere [Support multiple document views](../extensibility/supporting-multiple-document-views.md).

 L'IDE invia una notifica alle visualizzazioni relative agli eventi , ad esempio quando una soluzione contenente un documento viene chiusa, abbinando un identificatore di elemento (ItemID) per ogni voce nella tabella del documento in esecuzione. Per altre informazioni, vedere Running [document table](../extensibility/internals/running-document-table.md).

 Esistono due opzioni per la creazione di una visualizzazione per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la visualizzazione è ospitata in una finestra usando un controllo ActiveX o un oggetto dati del documento. Il secondo è il modello di incorporamento semplificato, in cui la visualizzazione è ospitata da e viene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> implementata per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [Attivazione sul posto](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Per informazioni sul modello di incorporamento semplificato, vedere [Incorporamento semplificato](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Vedi anche

- [Supporto di più visualizzazioni di documenti](../extensibility/supporting-multiple-document-views.md)
- [Incorporamento semplificato](../extensibility/simplified-embedding.md)
- [Procedura: Associare visualizzazioni ai dati del documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Gestione del titolare del blocco dei documenti](../extensibility/document-lock-holder-management.md)
- [Visualizzazioni singole e a più schede](../extensibility/single-and-multi-tab-views.md)
- [Salvare un documento standard](../extensibility/internals/saving-a-standard-document.md)
- [Persistenza e tabella del documento in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Determinare quale editor apre un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)