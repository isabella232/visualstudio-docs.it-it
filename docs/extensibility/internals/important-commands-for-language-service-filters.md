---
title: Comandi importanti per i filtri dei servizi di linguaggio | Microsoft Docs
description: Informazioni sui comandi importanti che è necessario supportare quando si crea un filtro completo del servizio di linguaggio in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d27f1c3057266d1b167999f3178a3e554a78ddb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069556"
---
# <a name="important-commands-for-language-service-filters"></a>Comandi importanti per i filtri dei servizi di linguaggio
Se si desidera creare un filtro dei servizi di linguaggio completo, considerare la possibilità di gestire i comandi seguenti. L'elenco completo degli identificatori di comando è definito nell' <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumerazione per il codice gestito e nel file di intestazione Stdidcmd. h per il [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] codice non gestito. È possibile trovare il file Stdidcmd. h nel *percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Comandi da gestire

> [!NOTE]
> Non è obbligatorio filtrare per ogni comando della tabella seguente.

|Comando|Descrizione|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente fa clic con il pulsante destro del mouse. Questo comando indica che è il momento di fornire un menu di scelta rapida. Se non si gestisce questo comando, l'editor di testo fornisce un menu di scelta rapida predefinito senza comandi specifici della lingua. Per includere comandi personalizzati in questo menu, gestire il comando e visualizzare un menu di scelta rapida.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Viene in genere inviato quando l'utente digita CTRL + J. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per visualizzare la casella di completamento dell'istruzione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita un carattere. Monitorare questo comando per determinare quando viene digitato un carattere di trigger e fornire il completamento delle istruzioni, i suggerimenti per il metodo e i marcatori di testo, ad esempio la colorazione della sintassi, la corrispondenza tra parentesi graffe e i marcatori di errore. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per il completamento dell'istruzione e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> per i suggerimenti del metodo. Per supportare i marcatori di testo, monitorare questo comando per determinare se il carattere digitato richiede di aggiornare i marcatori.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto INVIO. Monitorare questo comando per determinare quando ignorare una finestra del suggerimento del metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto BACKSPACE. Monitoraggio per determinare quando ignorare una finestra del suggerimento del metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu o un tasto di scelta rapida. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo sull'oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiornare la finestra del suggerimento con le informazioni sul parametro.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente passa su una variabile o posiziona il cursore su una variabile e seleziona **informazioni rapide** da **IntelliSense** nel menu **modifica** . Restituisce il tipo della variabile in un suggerimento chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Se il debug è attivo, il suggerimento deve anche visualizzare il valore della variabile.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Viene in genere inviato quando l'utente digita CTRL + barra SPAZIAtrice. Questo comando indica al servizio di linguaggio di chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu, in genere la selezione di **Commenti** o la rimozione di **Commenti** dal menu **Avanzate** nel menu **modifica** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente desidera impostare come commento il testo selezionato. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente desidera rimuovere il commento dal testo selezionato. Questi comandi possono essere implementati solo dal servizio di linguaggio.|

## <a name="see-also"></a>Vedi anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
