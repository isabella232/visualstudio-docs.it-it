---
title: Visualizzazione dei dati e dei documenti negli editor personalizzati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d4b14558a435d6ad9da32726508d81185961410
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414464"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Documenti e visualizzazione dei documenti negli editor personalizzati
Un editor personalizzato è costituito da due parti: un oggetto dati del documento e un oggetto visualizzazione del documento. Come suggerisce il nome, l'oggetto dati del documento rappresenta i dati di testo da visualizzare. Analogamente, l'oggetto visualizzazione documento (o "visualizzazione") rappresenta una o più finestre in cui visualizzare l'oggetto dati del documento.

## <a name="document-data-object"></a>Oggetto dati documento
 Un oggetto dati del documento è una rappresentazione di dati del testo nel buffer di testo. Si tratta di un oggetto COM che archivia il testo del documento e altre informazioni. L'oggetto dati del documento gestisce inoltre la persistenza del documento e Abilita più visualizzazioni dei dati. Per ulteriori informazioni, vedere

 <xref:EnvDTE80.Window2.DocumentData%2A> e [finestre del documento](../extensibility/internals/document-windows.md).

 Gli editor e le finestre di progettazione personalizzati possono scegliere di utilizzare l' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto o il relativo buffer personalizzato. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> segue il modello di incorporamento semplificato per un editor standard, supporta più visualizzazioni e fornisce le interfacce eventi usate per gestire più visualizzazioni.

## <a name="document-view-object"></a>Oggetto visualizzazione documento
 Una finestra che Visualizza codice e altro testo è nota come visualizzazione o visualizzazione del documento. Quando si crea un editor, è possibile scegliere una singola visualizzazione, in cui il testo viene visualizzato in una singola finestra. In alternativa, è possibile scegliere una visualizzazione multipla, in cui il testo viene visualizzato in più di una finestra. La scelta dipende dall'applicazione. Se ad esempio è necessario modificare side-by-Side, scegliere visualizzazione multipla. Ogni visualizzazione è associata a una voce Integrated Development Environment nella tabella documenti (IDE) in esecuzione (RDT). Le finestre di visualizzazione appartengono a un progetto o a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oggetto.

 Se l'editor supporta più visualizzazioni di un oggetto dati del documento, gli oggetti dati del documento e visualizzazione documento devono essere distinti. In caso contrario, è possibile raggrupparli insieme. Per altre informazioni, vedere [supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

 L'IDE notifica le visualizzazioni sugli eventi (ad esempio, quando una soluzione contenente un documento viene chiusa) associando un identificatore di elemento (ItemID) per ogni voce nella tabella documenti in esecuzione. Per altre informazioni, vedere esecuzione della [tabella documenti](../extensibility/internals/running-document-table.md).

 Sono disponibili due opzioni per la creazione di una vista per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la vista è ospitata in una finestra utilizzando un controllo ActiveX o un oggetto dati del documento. Il secondo è il modello di incorporamento semplificato, in cui la vista è ospitata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ed <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> è implementata per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [attivazione sul posto](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Per informazioni sul modello di incorporamento semplificato, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Vedere anche

- [Supportare più visualizzazioni di documenti](../extensibility/supporting-multiple-document-views.md)
- [Incorporamento semplificato](../extensibility/simplified-embedding.md)
- [Procedura: aggiungere visualizzazioni ai dati del documento](../extensibility/how-to-attach-views-to-document-data.md)
- [Gestione dei contenitori di blocco del documento](../extensibility/document-lock-holder-management.md)
- [Visualizzazioni singole e a più schede](../extensibility/single-and-multi-tab-views.md)
- [Salvare un documento standard](../extensibility/internals/saving-a-standard-document.md)
- [Persistenza e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Determinare quale editor apre un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)