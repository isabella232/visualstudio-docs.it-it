---
title: Dati del documento e visualizzazione del documento negli editor personalizzati Documenti Microsoft
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
ms.openlocfilehash: 04e89194ff09bc273294246cc25718c999daf70f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712142"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dati del documento e visualizzazione del documento negli editor personalizzati
Un editor personalizzato è costituito da due parti: un oggetto dati del documento e un oggetto visualizzazione documento. Come suggeriscono i nomi, l'oggetto dati del documento rappresenta i dati di testo da visualizzare. Analogamente, l'oggetto visualizzazione documento (o "visualizzazione") rappresenta una o più finestre in cui visualizzare l'oggetto dati del documento.

## <a name="document-data-object"></a>Oggetto dati del documento
 Un oggetto dati del documento è una rappresentazione dei dati del testo nel buffer di testo. Si tratta di un oggetto COM che archivia il testo del documento e altre informazioni. L'oggetto dati del documento gestisce inoltre la persistenza del documento e abilita più visualizzazioni dei dati. Per ulteriori informazioni, vedere

 <xref:EnvDTE80.Window2.DocumentData%2A>e [Documentare Windows](../extensibility/internals/document-windows.md).

 Gli editor personalizzati e i progettisti <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> possono scegliere di utilizzare l'oggetto o il proprio buffer personalizzato. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>segue il modello di incorporamento semplificato per un editor standard, supporta più visualizzazioni e fornisce interfacce di eventi utilizzate per gestire più visualizzazioni.

## <a name="document-view-object"></a>Oggetto visualizzazione documento
 Una finestra che visualizza codice e altro testo è nota come visualizzazione documento o visualizzazione. Quando si crea un editor, è possibile scegliere una singola visualizzazione, in cui il testo viene visualizzato in un'unica finestra. In alternativa, è possibile scegliere una visualizzazione multipla, in cui il testo viene visualizzato in più finestre. La scelta dipende dall'applicazione. Ad esempio, se è necessaria la modifica affiancata, è necessario scegliere più visualizzazioni. Ogni visualizzazione è associata a una voce nella tabella dei documenti in esecuzione (RDT) dell'ambiente di sviluppo integrato (IDE). Le finestre di visualizzazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> appartengono a un progetto o a un oggetto.

 Se l'editor supporta più visualizzazioni di un oggetto dati del documento, i dati del documento e gli oggetti visualizzazione documento devono essere separati. In caso contrario, possono essere raggruppati. Per ulteriori informazioni, consultate [Supporto di più visualizzazioni documento.](../extensibility/supporting-multiple-document-views.md)

 L'IDE notifica le visualizzazioni sugli eventi (ad esempio, quando una soluzione contenente un documento viene chiusa) facendo corrispondere un identificatore di elemento (ItemID) per ogni voce nella tabella del documento in esecuzione. Per ulteriori informazioni, vedere [Esecuzione della tabella documenti](../extensibility/internals/running-document-table.md).

 Sono disponibili due opzioni per la creazione di una visualizzazione per un editor personalizzato. Uno è il modello di attivazione sul posto, in cui la visualizzazione è ospitata in una finestra utilizzando un controllo ActiveX o un oggetto dati del documento. Il secondo è il modello di incorporamento semplificato, in cui la visualizzazione è ospitata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> viene implementata per gestire i comandi della finestra. Per informazioni sul modello di attivazione sul posto, vedere [Attivazione](/visualstudio/misc/in-place-activation?view=vs-2015)sul posto . Per informazioni sul modello di incorporamento semplificato, consultate [Incorporamento semplificato.](../extensibility/simplified-embedding.md)

## <a name="see-also"></a>Vedere anche

- [Supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md)
- [Incorporamento semplificato](../extensibility/simplified-embedding.md)
- [Procedura: associare visualizzazioni ai dati del documentoHow to: Attach views to document data](../extensibility/how-to-attach-views-to-document-data.md)
- [Gestione dei titolari dei blocchi di documenti](../extensibility/document-lock-holder-management.md)
- [Visualizzazioni a scheda singola e multipla](../extensibility/single-and-multi-tab-views.md)
- [Salvare un documento standard](../extensibility/internals/saving-a-standard-document.md)
- [Persistenza e tabella documenti in esecuzione](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Determinare quale editor apre un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)
