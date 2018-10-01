---
title: Eseguire il debug di un controllo WebView | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6b75f9dadbe1223c41989ff148028a355157bff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527685"
---
# <a name="debug-a-webview-control"></a>Debug di un controllo WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [eseguire il Debug di un controllo WebView](https://docs.microsoft.com/visualstudio/debugger/debug-a-webview-control).  
  
Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Per esaminare ed eseguire il debug dei controlli `WebView` in un'app di Windows Runtime, puoi configurare Visual Studio in modo da collegare Script Debugger all'avvio dell'app. A partire da Visual Studio 2013 Update 2, sono disponibili due modi per interagire con i controlli `WebView` tramite il debugger:  
  
-   Aprire il [DOM Explorer](../debugger/quickstart-debug-html-and-css.md) per un `WebView` , istanza ed esamina gli elementi DOM e analizzare i problemi di stile CSS sottoposto a rendering in modo dinamico le modifiche apportate agli stili di test.  
  
-   Selezionare la pagina Web o `iFrame` visualizzati nei `WebView` istanza come destinazione nel [JavaScript Console](../debugger/javascript-console-commands.md) finestra e quindi interagire con la pagina Web usando i comandi della console. La console consente di accedere al contesto di esecuzione dello script corrente.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Collegare il debugger (C#, Visual Basic, C++)  
  
1.  In Visual Studio, aggiungi un controllo `WebView` all'app di Windows Runtime.  
  
2.  In Esplora soluzioni, aprire le proprietà per il progetto scegliendo **proprietà** dal menu di scelta rapida per il progetto.  
  
3.  Scegli **Debug**. Nel **processo dell'applicazione** casella di riepilogo **Script**.  
  
     ![Collegare il debugger di script](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Facoltativo) Per le versioni non Express di Visual Studio, disabilitare il debug just-in-time (JIT) scegliendo **degli strumenti**, **opzioni**, **debug**, **Just-In-Time**, e quindi disabilitando il debug JIT per Script.  
  
    > [!NOTE]
    >  Disabilitando il debug JIT, puoi nascondere le finestre di dialogo per le eccezioni non gestite che si verificano in alcune pagine Web. In Visual Studio Express, il debug JIT è sempre disabilitato.  
  
5.  Premere F5 per avviare il debug.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usare DOM Explorer per esaminare ed eseguire il debug di un controllo WebView  
  
1.  (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.  
  
2.  Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.  
  
3.  Passa alla pagina contenente i controlli `Webview`.  
  
4.  Aprire la finestra di DOM Explorer per il `WebView` controllo scegliendo **Debug**, **Windows**, **DOM Explorer**e quindi scegliere l'URL del `WebView` che si Se si desidera esaminare.  
  
     ![Apertura di DOM Explorer](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     La finestra di DOM Explorer associata al controllo `WebView` viene visualizzata come nuova scheda in Visual Studio.  
  
5.  Visualizzare e modificare gli elementi DOM attivi e gli stili CSS come descritto in [stili Debug CSS tramite DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usare la finestra Console JavaScript per esaminare ed eseguire il debug di un controllo WebView  
  
1.  (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.  
  
2.  Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.  
  
3.  Aprire la finestra JavaScript Console per la `WebView` controllo scegliendo **Debug**, **Windows**, **JavaScript Console**.  
  
     La finestra Console JavaScript viene visualizzata.  
  
4.  Passa alla pagina contenente i controlli `Webview`.  
  
5.  Nella finestra della Console, selezionare la pagina Web o un' `iFrame` visualizzato per il `WebView` controllare nel **destinazione** elenco.  
  
     ![Selezione nella finestra della console JavaScript di destinazione](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Tramite la console puoi interagire con un singolo `WebView`, `iFrame`, contratto di condivisione o Web worker alla volta. Ogni elemento richiede un'istanza separata dell'host della piattaforma Web (WWAHost.exe). Puoi interagire con un solo host alla volta.  
  
6.  Visualizzare e modificare le variabili nell'app o usare i comandi della console, come descritto in [Guida introduttiva: eseguire il Debug JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) e [JavaScript Console commands](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)



