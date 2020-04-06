---
title: Documento di Windows Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708508"
---
# <a name="document-windows"></a>Finestre dei documenti
In Visual Studio, una finestra di *documento* è una finestra figlio con frame associata a una finestra di interfaccia a documenti multipli (MDI). Le finestre di documento vengono in genere utilizzate per la visualizzazione e la modifica del codice sorgente o del testo, ma possono anche ospitare altri tipi di funzionalità. Finestre documento:

- Può essere organizzato in gruppi di schede orizzontali o verticali separati nell'unità MDI padre in modo che più file possano essere visualizzati contemporaneamente.

- Può essere ancorato in qualsiasi ordine nell'mDI padre.

- Può essere galleggiato liberamente.

- Sono collegati in ordine di tabulazione ad altre finestre MDI.

  I comandi per il raggruppamento, l'ancoraggio e la modalità mobile sono disponibili nel menu di scelta rapida per una scheda della finestra del documento.

  Per ulteriori informazioni sul comportamento delle finestre in Visual Studio, consultate [Personalizzare i layout delle finestre.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Implementazione della finestra del documento
 Le finestre di documento vengono create implementando un editor. L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> crea finestre di documento come parte della creazione di un'istanza di un editor. Per ulteriori informazioni, vedere [Interfacce legacy nell'editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Per fornire punti di spostamento avanti e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> indietro in una finestra, implementare l'interfaccia. L'editor di testo utilizza marcatori di testo per identificare i punti di navigazione nel documento.

## <a name="the-running-document-table"></a>Tabella documenti in esecuzione
 L'IDE utilizza la tabella documenti in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. RDT è il meccanismo tramite il quale le finestre di documento vengono notificate agli eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per ulteriori informazioni, vedere [Esecuzione della tabella documenti.](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>Vedere anche
- [Caricamento ritardato dei documenti](../../extensibility/internals/delayed-document-loading.md)
