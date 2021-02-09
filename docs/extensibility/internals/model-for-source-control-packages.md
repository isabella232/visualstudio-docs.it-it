---
title: Modello per i pacchetti del controllo del codice sorgente | Microsoft Docs
description: Questo modello rappresenta un'implementazione del controllo del codice sorgente. In questo articolo vengono illustrati i nomi delle classi per semplificare la visualizzazione del modo in cui viene eseguito il controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 958465fc927464c46befb2422eb1286cda156916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895661"
---
# <a name="model-for-source-control-packages"></a>Modello per i pacchetti del controllo del codice sorgente
Il modello seguente rappresenta un esempio di implementazione del controllo del codice sorgente. Nel modello vengono visualizzate le interfacce che è necessario implementare e i servizi dell'ambiente che devono essere chiamati. Come tutti i servizi, si chiamano effettivamente i metodi di una particolare interfaccia ottenuti tramite il servizio. Vengono identificati i nomi delle classi per semplificare la visualizzazione del modo in cui viene eseguito il controllo del codice sorgente.

 ![Esempi di impostato di SCC&#95;](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Esempio di progetto di controllo del codice sorgente

## <a name="interfaces"></a>Interfacce
 È possibile implementare il controllo del codice sorgente per i nuovi tipi di progetto in Visual Studio usando l'elenco di interfacce illustrato nella tabella seguente.

|Interfaccia|Uso|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chiamato da progetti ed editor prima di salvare o modificare i file (Dirty). È possibile accedere a questa interfaccia tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chiamato dai progetti per richiedere l'autorizzazione per aggiungere, rimuovere o rinominare un file o una directory. Questa interfaccia viene chiamata anche dai progetti per informare l'ambiente quando viene completata un'azione di aggiunta, rimozione o ridenominazione approvata. È possibile accedervi usando il <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementata da qualsiasi entità registrata per ricevere una notifica quando i progetti aggiungono, rinominano o rimuovono un file o una directory. Per eseguire la registrazione per la notifica degli eventi, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Viene chiamato dai progetti per la registrazione con il pacchetto del controllo del codice sorgente e per ottenere informazioni sullo stato del controllo del codice sorgente. È possibile accedere a questa interfaccia tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementato dal progetto per rispondere alle richieste di controllo del codice sorgente per ottenere informazioni sui file e per ottenere le impostazioni di controllo del codice sorgente necessarie per il file di progetto.|

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
