---
title: Comandi importanti per i filtri del servizio di linguaggio | Microsoft Docs
description: Informazioni sui comandi importanti che è consigliabile supportare quando si crea un filtro del servizio di linguaggio completo in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 995cc17117f695500115a918ed24efc447855340dcb37e6b1dff8f9efa23638e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388630"
---
# <a name="important-commands-for-language-service-filters"></a>Comandi importanti per i filtri dei servizi di linguaggio
Se si vuole creare un filtro del servizio di linguaggio completamente in primo piano, è consigliabile gestire i comandi seguenti. L'elenco completo degli identificatori di comando è definito nell'enumerazione per il codice gestito e nel file di intestazione <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Stdidcmd.h per il codice non [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] gestito. Il file Stdidcmd.h è disponibile nel Visual Studio di installazione *dell'SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Comandi da gestire

> [!NOTE]
> Non è obbligatorio filtrare per ogni comando nella tabella seguente.

|Comando|Descrizione|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente fa clic con il pulsante destro del mouse. Questo comando indica che è il momento di fornire un menu di scelta rapida. Se non si gestisce questo comando, l'editor di testo fornisce un menu di scelta rapida predefinito senza comandi specifici del linguaggio. Per includere comandi personalizzati in questo menu, gestire il comando e visualizzare un menu di scelta rapida manualmente.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente preme CTRL+J. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo su per visualizzare la casella di completamento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dell'istruzione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente tipo un carattere. Monitorare questo comando per determinare quando viene digitato un carattere trigger e per fornire il completamento dell'istruzione, i suggerimenti dei metodi e gli indicatori di testo, ad esempio la colorazione della sintassi, la corrispondenza delle parentesi graffe e i marcatori di errore. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo sul completamento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dell'istruzione for e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> il metodo su per i suggerimenti del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> metodo. Per supportare gli indicatori di testo, monitorare questo comando per determinare se il carattere digitato richiede l'aggiornamento dei marcatori.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto INVIO. Monitorare questo comando per determinare quando chiudere una finestra di suggerimento del metodo chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> il metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Per impostazione predefinita, la visualizzazione testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente tipi la chiave Backspace. Monitorare per determinare quando chiudere una finestra di suggerimento del metodo chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> il metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Per impostazione predefinita, la visualizzazione testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu o da un tasto di scelta rapida. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo su per aggiornare la finestra di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> suggerimento con le informazioni sui parametri.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente passa il mouse su una variabile o posiziona il cursore su una variabile e seleziona **Informazioni** rapide da **IntelliSense** nel menu **Modifica.** Restituire il tipo della variabile in un suggerimento chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Se il debug è attivo, il suggerimento dovrebbe mostrare anche il valore della variabile.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere viene inviato quando l'utente preme CTRL+BARRA SPAZIATRICE. Questo comando indica al servizio di linguaggio di chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> il metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu, in genere **Comment Selection** (Selezione commenti) o **Uncomment Selection** from Advanced (Rimozione commento selezione da **Avanzate)** nel menu **Edit (Modifica).** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente vuole impostare come commento il testo selezionato. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente vuole rimuovere il commento dal testo selezionato. Questi comandi possono essere implementati solo dal servizio di linguaggio.|

## <a name="see-also"></a>Vedi anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
