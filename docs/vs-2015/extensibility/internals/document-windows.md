---
title: Documentazione di Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4e4a2a5c502058835d59793d2e22107ff3c07d5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241059"
---
# <a name="document-windows"></a>Finestre dei documenti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In Visual Studio, un *finestra di documento* è una finestra cornice figlio associato a una finestra di interfaccia a documenti multipli (MDI). Le finestre dei documenti vengono generalmente utilizzate per la visualizzazione e modifica di codice sorgente o di testo, ma che possono ospitare anche altri tipi di funzionalità. Finestre dei documenti:  
  
-   È possibile organizzare in gruppi di scheda separata orizzontale o verticale del padre MDI in modo che più file possono essere visualizzati nello stesso momento.  
  
-   Possono essere ancorate in qualsiasi ordine del padre MDI.  
  
-   Possono essere spostate liberamente.  
  
-   Sono collegate in ordine di tabulazione per le altre finestre MDI.  
  
 Comandi per il raggruppamento, ancorate e mobili sono disponibili nel menu di scelta rapida per una scheda della finestra documento.  
  
 Per altre informazioni sul comportamento delle finestre in Visual Studio, vedere [personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementazione della finestra documento  
 Le finestre dei documenti vengono create implementando un editor. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia consente di creare finestre di documento come parte di un'istanza di un editor. Per altre informazioni, vedere [interfacce Legacy nell'Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Per fornire all'indietro e inoltrare i punti di navigazione in una finestra, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaccia. L'editor di testo Usa marcatori di testo per identificare i punti di navigazione nel documento.  
  
## <a name="the-running-document-table"></a>Nella tabella documenti in esecuzione  
 L'IDE Usa la tabella documenti in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. RDT è il meccanismo tramite quale documento windows ricevono una notifica degli eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per altre informazioni, vedere [tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Caricamento dei documenti ritardato](../../extensibility/internals/delayed-document-loading.md)

