---
title: Modello per i pacchetti di controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707066"
---
# <a name="model-for-source-control-packages"></a>Modello per i pacchetti del controllo del codice sorgente
Il modello seguente rappresenta un esempio di implementazione del controllo del codice sorgente. Nel modello vengono visualizzate le interfacce che è necessario implementare e i servizi di ambiente che è necessario chiamare. Come tutti i servizi, in realtà si chiamano i metodi di una particolare interfaccia che si ottiene tramite il servizio. I nomi delle classi vengono identificati per semplificare la visualizzazione delle modalità di gestione del controllo del codice sorgente.

 ![Esempi di SCC&#95;TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Esempio di progetto di controllo del codice sorgenteExample Source Control Project

## <a name="interfaces"></a>Interfacce
 È possibile implementare il controllo del codice sorgente per i nuovi tipi di progetto in Visual Studio usando l'elenco delle interfacce illustrato nella tabella seguente.

|Interfaccia|Uso|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chiamato da progetti ed editor prima di salvare o modificare i file (dirty). Si accede a <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> questa interfaccia tramite il servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chiamato dai progetti per richiedere l'autorizzazione per aggiungere, rimuovere o rinominare un file o una directory. Questa interfaccia viene chiamata anche dai progetti per informare l'ambiente quando un'azione di aggiunta, rimozione o ridenominazione approvata è stata completata. Vi si accede <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> tramite il servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementato da qualsiasi entità che registra la notifica quando i progetti aggiungono, rinominano o rimuovono un file o una directory. Per effettuare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>registrazione per la notifica degli eventi, chiamare .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chiamato dai progetti per la registrazione con il pacchetto del controllo del codice sorgente e per ottenere informazioni sullo stato del controllo del codice sorgente. Si accede a <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> questa interfaccia tramite il servizio.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementato dal progetto per rispondere alle richieste del controllo del codice sorgente per informazioni sui file e per ottenere le impostazioni del controllo del codice sorgente necessarie per il file di progetto.|

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
