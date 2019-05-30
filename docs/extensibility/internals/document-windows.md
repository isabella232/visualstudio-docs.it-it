---
title: Documentazione di Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 844176b2db6074a33ac2e612c47d3779031836df
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345471"
---
# <a name="document-windows"></a>Finestre dei documenti
In Visual Studio, un *finestra di documento* è una finestra cornice figlio associato a una finestra di interfaccia a documenti multipli (MDI). Le finestre dei documenti vengono generalmente utilizzate per la visualizzazione e modifica di codice sorgente o di testo, ma che possono ospitare anche altri tipi di funzionalità. Finestre dei documenti:

- È possibile organizzare in gruppi di scheda separata orizzontale o verticale del padre MDI in modo che più file possono essere visualizzati nello stesso momento.

- Possono essere ancorate in qualsiasi ordine del padre MDI.

- Possono essere spostate liberamente.

- Sono collegate in ordine di tabulazione per le altre finestre MDI.

  Comandi per il raggruppamento, ancorate e mobili sono disponibili nel menu di scelta rapida per una scheda della finestra documento.

  Per altre informazioni sul comportamento delle finestre in Visual Studio, vedere [personalizzare i layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementazione della finestra documento
 Le finestre dei documenti vengono create implementando un editor. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia consente di creare finestre di documento come parte di un'istanza di un editor. Per altre informazioni, vedere [Legacy interfacce nell'editor](../../extensibility/legacy-interfaces-in-the-editor.md).

> [!NOTE]
> Per fornire all'indietro e inoltrare i punti di navigazione in una finestra, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaccia. L'editor di testo Usa marcatori di testo per identificare i punti di navigazione nel documento.

## <a name="the-running-document-table"></a>Nella tabella documenti in esecuzione
 L'IDE Usa la tabella documenti in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. RDT è il meccanismo tramite quale documento windows ricevono una notifica degli eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per altre informazioni, vedere [in esecuzione tabella document](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Vedere anche
- [Caricamento dei documenti ritardato](../../extensibility/internals/delayed-document-loading.md)