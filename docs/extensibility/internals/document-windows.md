---
title: Finestre documento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708508"
---
# <a name="document-windows"></a>Finestre dei documenti
In Visual Studio una *finestra del documento* è una finestra figlio incorniciata associata a una finestra interfaccia a documenti multipli (MDI). Le finestre di documento vengono in genere usate per la visualizzazione e la modifica del codice sorgente o del testo, ma possono anche ospitare altri tipi funzionali. Finestre di documento:

- Può essere organizzato in gruppi di schede orizzontali o verticali distinti nell'MDI padre, in modo che più file possano essere visualizzati contemporaneamente.

- Può essere ancorato in qualsiasi ordine nell'elemento MDI padre.

- È possibile fluttuare liberamente.

- Sono collegati in ordine di tabulazione ad altre finestre MDI.

  I comandi per il raggruppamento, l'ancoraggio e la virgola mobile sono disponibili nel menu di scelta rapida per una scheda della finestra del documento.

  Per altre informazioni sul comportamento delle finestre in Visual Studio, vedere [personalizzare il layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Implementazione della finestra del documento
 Le finestre di documento vengono create implementando un editor. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia crea le finestre del documento come parte della creazione di un'istanza di un editor. Per ulteriori informazioni, vedere [interfacce legacy nell'editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Per fornire punti di navigazione indietro e avanti in una finestra, implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> interfaccia. Nell'editor di testo vengono utilizzati marcatori di testo per identificare i punti di navigazione nel documento.

## <a name="the-running-document-table"></a>Tabella documenti in esecuzione
 L'IDE utilizza la tabella documenti in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. RDT è il meccanismo tramite il quale le finestre del documento ricevono notifiche di eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per ulteriori informazioni, vedere [esecuzione della tabella documenti](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Vedere anche
- [Caricamento ritardato dei documenti](../../extensibility/internals/delayed-document-loading.md)
