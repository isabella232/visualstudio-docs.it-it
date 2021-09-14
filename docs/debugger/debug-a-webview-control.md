---
title: Eseguire il debug di un controllo WebView (UWP) | Microsoft Docs
description: Informazioni su come esaminare ed eseguire il debug dei controlli WebView usati in un'app Windows Runtime. È possibile usare il DOM Explorer e la finestra della console JavaScript.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 3198685acc8ad33a545bf55628c99e78d104d251
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630809"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Eseguire il debug di un controllo WebView in un'app UWP

 Per esaminare ed eseguire il debug dei controlli `WebView` in un'app di Windows Runtime, puoi configurare Visual Studio in modo da collegare Script Debugger all'avvio dell'app. È possibile interagire con i controlli `WebView` usando il debugger in due modi:

- Aprire [DOM Explorer`WebView` per un'istanza di ](../debugger/quickstart-debug-html-and-css.md) ed esaminare gli elementi DOM, controllare i problemi relativi allo stile CSS e sottoporre a test le modifiche apportate agli stili con rendering dinamico.

- Selezionare la pagina Web o l'`iFrame` visualizzato nell'istanza di `WebView` come destinazione nella finestra [Console JavaScript](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) e quindi interagire con la pagina Web usando i comandi della console. La console consente di accedere al contesto di esecuzione dello script corrente.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Collegare il debugger (C#, Visual Basic, C++)

1. In Visual Studio, aggiungi un controllo `WebView` all'app di Windows Runtime.

2. In Esplora soluzioni aprire le proprietà del progetto scegliendo **Proprietà** nel menu di scelta rapida del progetto.

3. Scegliere **Debug**. Nell'elenco **Processo applicativo** scegliere **Script**.

     ![Collegamento del debugger di script](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. (Facoltativo) Per le versioni non Express di Visual Studio, disabilitare il debug just-in-time (JIT) scegliendo **Strumenti > Opzioni > Debug > Just-In-Time** e quindi disabilitando il debug JIT per Script.

    > [!NOTE]
    > Disabilitando il debug JIT, puoi nascondere le finestre di dialogo per le eccezioni non gestite che si verificano in alcune pagine Web. In Visual Studio Express, il debug JIT è sempre disabilitato.

5. Premere F5 per avviare il debug.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Usare DOM Explorer per esaminare ed eseguire il debug di un controllo WebView

1. (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.

2. Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.

3. Passa alla pagina contenente i controlli `Webview`.

4. Aprire la finestra di DOM Explorer per il controllo `WebView` scegliendo **Debug**, **Finestre**, **DOM Explorer** e quindi scegliere l'URL del controllo `WebView` che si vuole esaminare.

     ![Apertura di DOM Explorer](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     La finestra di DOM Explorer associata al controllo `WebView` viene visualizzata come nuova scheda in Visual Studio.

5. Visualizzare e modificare gli elementi DOM live e gli stili CSS, come descritto in [Eseguire il debug di stili CSS usando DOM Explorer](quickstart-debug-html-and-css.md).

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Usare la finestra Console JavaScript per esaminare ed eseguire il debug di un controllo WebView

1. (C#, Visual Basic, C++) Collega Script Debugger all'app. Per istruzioni consulta la prima sezione.

2. Se non l'hai già fatto, aggiungi un controllo `WebView` all'app e premi F5 per avviare il debug.

3. Aprire la finestra Console JavaScript per il controllo `WebView` scegliendo **Debug**, **Finestre**, **Console JavaScript**.

     La finestra Console JavaScript viene visualizzata.

4. Passa alla pagina contenente i controlli `Webview`.

5. Nella finestra Console selezionare la pagina Web o un `iFrame` visualizzato mediante il controllo `WebView` nell'elenco **Destinazione**.

     ![Selezione della destinazione nella finestra della console JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > Tramite la console puoi interagire con un singolo `WebView`, `iFrame`, contratto di condivisione o Web worker alla volta. Ogni elemento richiede un'istanza separata dell'host della piattaforma Web (WWAHost.exe). Puoi interagire con un solo host alla volta.

6. Visualizzare e modificare le variabili nell'app o usare i comandi della console, come descritto in [Guida introduttiva: Eseguire il debug](../debugger/quickstart-debug-javascript-using-the-console.md) dei comandi JavaScript e [JavaScript Console](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true).

## <a name="see-also"></a>Vedi anche

- [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)