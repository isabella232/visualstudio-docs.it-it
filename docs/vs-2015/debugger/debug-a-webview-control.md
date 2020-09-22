---
title: Eseguire il debug di un controllo WebView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f2da5b3122bd97fcbef0db7124049372c21983f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839903"
---
# <a name="debug-a-webview-control"></a>Debug di un controllo WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image windows_and_phone_content.png "windows_and_phone_content")  
  
 Per esaminare ed eseguire il debug dei controlli `WebView` in un'app di Windows Runtime, puoi configurare Visual Studio in modo da collegare Script Debugger all'avvio dell'app. A partire da Visual Studio 2013 Update 2, sono disponibili due modi per interagire con i controlli `WebView` tramite il debugger:  
  
- Aprire [DOM Explorer`WebView` per un'istanza di ](../debugger/quickstart-debug-html-and-css.md) ed esaminare gli elementi DOM, controllare i problemi relativi allo stile CSS e sottoporre a test le modifiche apportate agli stili con rendering dinamico.  
  
- Selezionare la pagina Web o l'`iFrame` visualizzato nell'istanza di `WebView` come destinazione nella finestra [Console JavaScript](../debugger/javascript-console-commands.md) e quindi interagire con la pagina Web usando i comandi della console. La console consente di accedere al contesto di esecuzione dello script corrente.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Collegare il debugger (C#, Visual Basic, C++)  
  
1. In Visual Studio, aggiungi un controllo `WebView` all'app di Windows Runtime.  
  
2. In Esplora soluzioni aprire le proprietà del progetto scegliendo **Proprietà** nel menu di scelta rapida del progetto.  
  
3. Scegliere **Debug**. Nell'elenco **Processo applicativo** scegliere **Script**.  
  
     ![Collegamento del debugger di script](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4. Opzionale Per le versioni non Express di Visual Studio, disabilitare il debug JIT (just-in-Time) scegliendo **strumenti**, **Opzioni**, **debug**, **just-in-Time**e quindi disabilitando il debug JIT per lo script.  
  
    > [!NOTE]
    > Disabilitando il debug JIT, puoi nascondere le finestre di dialogo per le eccezioni non gestite che si verificano in alcune pagine Web. In Visual Studio Express, il debug JIT è sempre disabilitato.  
  
5. Premere F5 per avviare il debug.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usare DOM Explorer per esaminare ed eseguire il debug di un controllo WebView  
  
1. (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.  
  
2. Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.  
  
3. Passa alla pagina contenente i controlli `Webview`.  
  
4. Aprire la finestra di DOM Explorer per il controllo `WebView` scegliendo **Debug**, **Finestre**, **DOM Explorer** e quindi scegliere l'URL del controllo `WebView` che si vuole esaminare.  
  
     ![Apertura di DOM Explorer](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     La finestra di DOM Explorer associata al controllo `WebView` viene visualizzata come nuova scheda in Visual Studio.  
  
5. Visualizzare e modificare gli elementi DOM attivi e gli stili CSS come descritto in [eseguire il debug di stili CSS usando Dom Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usare la finestra Console JavaScript per esaminare ed eseguire il debug di un controllo WebView  
  
1. (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.  
  
2. Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.  
  
3. Aprire la finestra Console JavaScript per il controllo `WebView` scegliendo **Debug**, **Finestre**, **Console JavaScript**.  
  
     La finestra Console JavaScript viene visualizzata.  
  
4. Passa alla pagina contenente i controlli `Webview`.  
  
5. Nella finestra Console selezionare la pagina Web o un `iFrame` visualizzato mediante il controllo `WebView` nell'elenco **Destinazione**.  
  
     ![Selezione della destinazione nella finestra della console JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    > Tramite la console puoi interagire con un singolo `WebView`, `iFrame`, contratto di condivisione o Web worker alla volta. Ogni elemento richiede un'istanza separata dell'host della piattaforma Web (WWAHost.exe). Puoi interagire con un solo host alla volta.  
  
6. Visualizzare e modificare le variabili nell'app o usare i comandi della console, come descritto in [Guida introduttiva: eseguire il debug](../debugger/quickstart-debug-javascript-using-the-console.md) dei [comandi della console](../debugger/javascript-console-commands.md)JavaScript e JavaScript.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
