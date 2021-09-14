---
title: Modello per i pacchetti di controllo del codice sorgente | Microsoft Docs
description: Questo modello rappresenta un'implementazione del controllo del codice sorgente. L'articolo mostra i nomi delle classi per semplificare la visualizzazione del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a43d1feb2dde67d6eae291490476db4b98850870
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636163"
---
# <a name="model-for-source-control-packages"></a>Modello per i pacchetti del controllo del codice sorgente
Il modello seguente rappresenta un esempio di implementazione di un controllo del codice sorgente. Nel modello vengono visualizzati le interfacce che è necessario implementare e i servizi di ambiente che è necessario chiamare. Come tutti i servizi, in realtà si chiamano i metodi di una particolare interfaccia che si ottiene tramite il servizio. I nomi delle classi vengono identificati per semplificare la visualizzazione del controllo del codice sorgente.

 ![Esempi di SCC&#95;TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Esempio di controllo del codice sorgente Project

## <a name="interfaces"></a>Interfacce
 È possibile implementare il controllo del codice sorgente per i nuovi tipi di progetto Visual Studio usando l'elenco di interfacce illustrato nella tabella seguente.

|Interfaccia|Uso|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chiamato da progetti ed editor prima di salvare o modificare i file (dirty). Questa interfaccia è accessibile tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> servizio .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chiamato dai progetti per richiedere l'autorizzazione per aggiungere, rimuovere o rinominare un file o una directory. Questa interfaccia viene chiamata anche dai progetti per informare l'ambiente quando viene completata un'azione di aggiunta, rimozione o ridenominazione approvata. È possibile accedervi usando il <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> servizio .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementato da qualsiasi entità che si registra per ricevere una notifica quando i progetti aggiungono, rinominano o rimuovono un file o una directory. Per eseguire la registrazione per la notifica degli eventi, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chiamato dai progetti per la registrazione con il pacchetto di controllo del codice sorgente e per ottenere informazioni sullo stato del controllo del codice sorgente. Questa interfaccia è accessibile tramite il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servizio .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementato dal progetto per rispondere alle richieste di informazioni sui file del controllo del codice sorgente e per ottenere le impostazioni del controllo del codice sorgente necessarie per il file di progetto.|

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
