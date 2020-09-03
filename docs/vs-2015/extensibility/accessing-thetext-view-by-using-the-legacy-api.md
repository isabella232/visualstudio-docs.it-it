---
title: Accesso alla vista theText tramite l'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184943"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Accesso alla visualizzazione testo tramite l'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una visualizzazione di testo è una presentazione del testo archiviato in un buffer di testo. È possibile accedere alla visualizzazione di testo usando l'API legacy, come illustrato nella sezione seguente.  
  
## <a name="text-view-object"></a>Oggetto visualizzazione di testo  
 Ogni visualizzazione è associata al proprio buffer di testo e la visualizzazione è una finestra sui dati nel buffer. Il diagramma seguente illustra le interfacce principali dell'oggetto visualizzazione di testo, rappresentato da <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Oggetto TextView di Visual Studio](../extensibility/media/vstextview.gif "oggetto VsTextView")  
Oggetto visualizzazione di testo  
  
 La visualizzazione è un modo per presentare il testo nel buffer. Include funzionalità quali il ritorno a capo automatico e la struttura, in modo che ciò che viene visualizzato nella visualizzazione non sia una rappresentazione esatta del testo nel buffer.  
  
 Una visualizzazione consente ad altri servizi o processi di intercettare i comandi in ingresso e di agire su di essi prima che la vista agisca su di essi. Il servizio più comune a tale scopo è un servizio di linguaggio. Potrebbe essere necessario, ad esempio, un servizio di linguaggio per intercettare il comando per il tasto INVIO per fornire un comportamento di rientro personalizzato o descrizioni comandi.  
  
## <a name="adding-functionality-to-the-text-view"></a>Aggiunta di funzionalità alla visualizzazione di testo  
 È possibile personalizzare il comportamento della visualizzazione di testo gestendo sequenze di tasti specifiche. Per intercettare le sequenze di tasti, implementare nell' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> oggetto e fornire una destinazione del comando ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) per monitorare e intercettare i comandi.  
  
 La visualizzazione di testo usa l'architettura sequenziale per i filtri dei comandi. I nuovi filtri dei comandi ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oggetti) vengono aggiunti alla sequenza chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo.  
  
 La notifica degli eventi per la visualizzazione di testo viene fornita tramite l' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfaccia. Implementare questa interfaccia nell'oggetto client per ricevere una notifica delle modifiche apportate alla visualizzazione di testo. Esporre questa interfaccia alla visualizzazione di testo utilizzando l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfaccia nella visualizzazione di testo per ricevere la notifica delle modifiche dalla vista.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica delle impostazioni di visualizzazione tramite l'API legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Uso della gestione testi per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
