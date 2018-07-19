---
title: L'accesso a theText visualizzazione tramite l'API Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fe57ab7ef5ac113f1248f89cd62ef5b9ec33ca3
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081823"
---
# <a name="access-the-text-view-by-using-the-legacy-api"></a>Accedere alla visualizzazione di testo usando l'API legacy
Una visualizzazione di testo è una presentazione del testo archiviato in un buffer di testo. È possibile accedere alla visualizzazione di testo con l'API legacy, come illustrato nella sezione seguente.

## <a name="text-view-object"></a>Oggetto visualizzazione di testo
 Ogni visualizzazione è associato un proprio buffer di testo e la visualizzazione è una finestra sui dati nel buffer. Il diagramma seguente mostra le interfacce principali dell'oggetto di visualizzazione del testo, che è rappresentato dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 ![Visualizzazione oggetto testo di Visual Studio](../extensibility/media/vstextview.gif "oggetto vstextview") oggetto visualizzazione di testo

 La vista è un modo per presentare il testo nel buffer. Include funzionalità quali ritorno a capo automatico e la modalità struttura, in modo che ciò che viene visualizzato nella vista non è una rappresentazione esatta del testo nel buffer.

 Una vista consente di altri servizi o processi per intercettare i comandi in ingresso e agire su di esse prima della visualizzazione interviene su di essi. Il servizio più comune per eseguire questa operazione è un servizio di linguaggio. Un servizio di linguaggio potrebbe essere necessario, ad esempio, di intercettare il comando per il tasto INVIO fornire suggerimenti di comportamento o lo strumento rientri personalizzati.

## <a name="add-functionality-to-the-text-view"></a>Aggiungere funzionalità alla visualizzazione di testo
 È possibile personalizzare il comportamento di visualizzazione di testo mediante la gestione di specifiche combinazioni di tasti. Per intercettare le pressioni di tasti, si implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sull'oggetto e fornire una destinazione comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) per monitorare e intercetta comandi.

 La visualizzazione di testo utilizza architettura sequenziale per i filtri di comando. Nuovi filtri di comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetti) vengono aggiunte alla sequenza chiamando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (metodo).

 Notifica degli eventi per la visualizzazione di testo viene fornita tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents> interfaccia. Implementare questa interfaccia sull'oggetto client di ricevere notifica delle modifiche apportate alla visualizzazione di testo. Esporre questa interfaccia per la visualizzazione di testo usando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia nella visualizzazione di testo per ricevere notifica delle modifiche apportate dalla vista.

## <a name="see-also"></a>Vedere anche

- [Modificare le impostazioni di visualizzazione tramite l'API legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)
- [Usare la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)