---
title: Documenti Windows | Microsoft Docs
description: Informazioni sulle finestre dei documenti Visual Studio, tra cui come implementarle e come la tabella di documenti in esecuzione (RDT) tiene traccia del relativo stato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc3fc77d895805eae1dbffb092721fc0c8dd616c63b796da42205e1e65c42ea9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376248"
---
# <a name="document-windows"></a>Finestre dei documenti
In Visual Studio, una *finestra del* documento è una finestra figlio con frame associata a una finestra dell'interfaccia a documenti multipli (MDI). Le finestre dei documenti vengono in genere usate per la visualizzazione e la modifica del codice sorgente o del testo, ma possono ospitare anche altri tipi funzionali. Finestre del documento:

- Può essere organizzato in gruppi di schede orizzontali o verticali separati nell'MDI padre in modo che più file possano essere visualizzati contemporaneamente.

- Può essere ancorato in qualsiasi ordine nell'MDI padre.

- Può essere mobile liberamente.

- Sono collegati in ordine di tabulazione ad altre finestre MDI.

  I comandi per il raggruppamento, l'ancoraggio e la virgola mobile sono disponibili nel menu di scelta rapida per una scheda della finestra del documento.

  Per altre informazioni sul comportamento delle finestre in Visual Studio, vedere [Personalizzare i layout delle finestre.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Implementazione della finestra del documento
 Le finestre dei documenti vengono create implementando un editor. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>L'interfaccia crea finestre di documento come parte della creazione di un'istanza di un editor. Per altre informazioni, vedere [Interfacce legacy nell'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Per fornire punti di spostamento indietro e avanti in una finestra, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> l'interfaccia . L'editor di testo usa gli indicatori di testo per identificare i punti di spostamento nel documento.

## <a name="the-running-document-table"></a>Tabella del documento In esecuzione
 L'IDE usa la tabella del documento in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. RDT è il meccanismo tramite il quale le finestre dei documenti vengono notificate di eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per altre informazioni, vedere [Esecuzione della tabella documento](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Vedi anche
- [Caricamento ritardato dei documenti](../../extensibility/internals/delayed-document-loading.md)
