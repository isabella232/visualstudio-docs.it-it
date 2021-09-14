---
title: Documento Windows | Microsoft Docs
description: Informazioni sulle finestre dei documenti in Visual Studio, tra cui come implementarle e come la tabella di documenti in esecuzione (RDT) tiene traccia del relativo stato.
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
ms.openlocfilehash: 1a1659bc97e1626e198b2a3867223005c84cf9e7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709581"
---
# <a name="document-windows"></a>Finestre dei documenti
In Visual Studio, una *finestra del* documento è una finestra figlio incorniciata associata a una finestra dell'interfaccia a documenti multipli (MDI). Le finestre dei documenti vengono in genere usate per la visualizzazione e la modifica del codice sorgente o del testo, ma possono anche ospitare altri tipi funzionali. Finestre dei documenti:

- Può essere organizzato in gruppi di schede orizzontali o verticali separati nell'MDI padre in modo che più file possano essere visualizzati contemporaneamente.

- Può essere ancorato in qualsiasi ordine nell'MDI padre.

- Può essere mobile liberamente.

- Sono collegati in ordine di tabulazione ad altre finestre MDI.

  I comandi per il raggruppamento, l'ancoraggio e la virgola mobile sono disponibili nel menu di scelta rapida per una scheda della finestra del documento.

  Per altre informazioni sul comportamento delle finestre in Visual Studio, vedere [Personalizzare il layout delle finestre.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>Implementazione della finestra del documento
 Le finestre dei documenti vengono create implementando un editor. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>L'interfaccia crea finestre di documento come parte della creazione di un'istanza di un editor. Per altre informazioni, vedere [Interfacce legacy nell'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015).

> [!NOTE]
> Per fornire punti di spostamento indietro e avanti in una finestra, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> l'interfaccia . L'editor di testo usa marcatori di testo per identificare i punti di spostamento nel documento.

## <a name="the-running-document-table"></a>Tabella dei documenti in esecuzione
 L'IDE usa la tabella di documenti in esecuzione (RDT) per tenere traccia dello stato di ogni finestra del documento. RDT è il meccanismo tramite il quale le finestre dei documenti vengono notificate di eventi, ad esempio quando una soluzione viene chiusa o quando un file è stato modificato. Per altre informazioni, vedere [Running document table](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Vedi anche
- [Caricamento ritardato dei documenti](../../extensibility/internals/delayed-document-loading.md)
