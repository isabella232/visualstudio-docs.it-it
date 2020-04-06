---
title: Comandi importanti per i filtri del servizio di linguaggio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707621"
---
# <a name="important-commands-for-language-service-filters"></a>Comandi importanti per i filtri dei servizi di linguaggio
Se si desidera creare un filtro del servizio di linguaggio completo, è consigliabile gestire i comandi seguenti. L'elenco completo degli identificatori <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> di comando è definito nell'enumerazione per il [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] codice gestito e nel file di intestazione Stdidcmd.h per il codice non gestito. È possibile trovare il file Stdidcmd.h nel percorso di installazione di *Visual Studio SDK.*

## <a name="commands-to-handle"></a>Comandi da gestire

> [!NOTE]
> Non è obbligatorio filtrare per ogni comando nella tabella seguente.

|Comando|Descrizione|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente fa clic con il pulsante destro del mouse. Questo comando indica che è il momento di fornire un menu di scelta rapida. Se non si gestisce questo comando, l'editor di testo fornisce un menu di scelta rapida predefinito senza comandi specifici della lingua. Per includere comandi personalizzati in questo menu, gestire il comando e visualizzare manualmente un menu di scelta rapida.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere, viene inviato quando l'utente digita CTRL. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> su per visualizzare la casella di completamento dell'istruzione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita un carattere. Monitorare questo comando per determinare quando viene digitato un carattere trigger e per fornire il completamento delle istruzioni, suggerimenti sul metodo e marcatori di testo, ad esempio la colorazione della sintassi, la corrispondenza delle parentesi graffe e gli indicatori di errore. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sul per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> il completamento dell'istruzione e il metodo sui suggerimenti per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> metodo . Per supportare i marcatori di testo, monitorate questo comando per determinare se il carattere digitato richiede l'aggiornamento dei marcatori.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto Invio. Monitorare questo comando per determinare quando chiudere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> una finestra <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>di suggerimento del metodo chiamando il metodo su . Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto Backspace. Monitorare per determinare quando chiudere una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> finestra di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>suggerimento del metodo chiamando il metodo su . Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu o da un tasto di scelta rapida. Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> su per aggiornare la finestra di suggerimento con le informazioni sui parametri.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente passa il mouse su una variabile o posiziona il cursore su una variabile e seleziona **Informazioni rapide** da **IntelliSense** nel menu **Modifica.** Restituire il tipo della variabile in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> un suggerimento chiamando il metodo su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Se il debug è attivo, il suggerimento dovrebbe mostrare anche il valore della variabile.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere viene inviato quando l'utente digita CTRL e la barra spaziatrice. Questo comando indica al servizio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>linguaggio di chiamare il metodo su .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu, in genere **Selezione commento** o **Rimuovi commento selezione** da **Avanzate** nel menu **Modifica.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica che l'utente desidera impostare come commento il testo selezionato; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente desidera rimuovere il commento dal testo selezionato. Questi comandi possono essere implementati solo dal servizio di linguaggio.|

## <a name="see-also"></a>Vedere anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
