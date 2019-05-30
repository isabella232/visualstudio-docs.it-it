---
title: Comandi importanti per il linguaggio di servizio filtri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73ecbad3578c356ed9f82f79cdf9144d4c2bd32d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335077"
---
# <a name="important-commands-for-language-service-filters"></a>Comandi importanti per i filtri dei servizi di linguaggio
Se si desidera creare un filtro di servizio di linguaggio completamente in primo piano, prendere in considerazione i seguenti comandi di gestione. L'elenco completo degli identificatori di comando è definito nel <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumerazione per codice gestito e l'intestazione Stdidcmd.h file per unmanaged [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] codice. È possibile trovare il file Stdidcmd.h *percorso di installazione di Visual Studio SDK*\visualstudiointegration\common\inc.

## <a name="commands-to-handle"></a>Comandi da Handle

> [!NOTE]
> Non è obbligatorio per filtrare per ogni comando nella tabella seguente.

|Comando|Descrizione|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente fa clic. Questo comando indica che è necessario fornire un menu di scelta rapida. Se non si gestisce questo comando, l'editor di testo fornisce un menu di scelta rapida predefinito senza i comandi specifici della lingua. Per includere i propri comandi in questo menu, gestire il comando e visualizzare un menu di scelta rapida personalizzati.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente digita CTRL + J. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> visualizzare la finestra di completamento istruzione.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita un carattere. Monitorare questo comando per determinare quando si digita un carattere di trigger e per fornire istruzione completamento, suggerimenti di metodo e marcatori di testo, ad esempio la colorazione della sintassi, corrispondenza parentesi e gli indicatori di errore. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per il completamento istruzioni e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodo sul <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> per suggerimenti di metodo. Per supportare i marcatori di testo, monitorare questo comando per determinare se il carattere viene digitato è necessario aggiornare i marcatori.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto INVIO. Monitorare questo comando per determinare il momento chiudere una finestra del suggerimento di metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto Backspace. Monitoraggio per determinare quando chiudere una finestra del suggerimento di metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu o un tasto di scelta rapida. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per aggiornare la finestra del suggerimento con le informazioni sui parametri.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente posiziona il mouse su una variabile o posiziona il cursore su una variabile e seleziona **informazioni rapide** dalla **IntelliSense** nel **Edit** menu. Restituire il tipo della variabile in un suggerimento chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Se il debug è attivo, il suggerimento visualizzerà il valore della variabile.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente digita CTRL + BARRA SPAZIATRICE. Questo comando indica al servizio di linguaggio per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo su di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu, in genere **Commenta selezione** oppure **Rimuovi commento selezione** da **avanzate** nel **modifica** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente desidera impostare come commento il testo selezionato. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica che l'utente desidera rimuovere il commento al testo selezionato. Questi comandi possono essere implementati solo dal servizio di linguaggio.|

## <a name="see-also"></a>Vedere anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)