---
title: Eseguire il debug di JavaScript usando la console | Microsoft Docs
description: Usare la finestra della console JavaScript Visual Studio per interagire con le app UWP (Universal Windows Platform) compilate con JavaScript.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- JavaScript
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6672e164978a97c4801c4d4d4481422a2c093582
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090499"
---
# <a name="debug-javascript-using-the-console-in-visual-studio"></a>Eseguire il debug di JavaScript usando la console in Visual Studio

È possibile usare la finestra della console JavaScript per interagire con le app UWP compilate con JavaScript ed eseguirne il debug. Queste funzionalità sono supportate per le app UWP e le app create usando Strumenti di Visual Studio per Apache Cordova. Per informazioni di riferimento sui comandi della console, vedi [JavaScript Console commands](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true).

La finestra Console JavaScript ti permette di:

- Inviare oggetti, valori e messaggi dalla tua app alla finestra della console.

- Visualizzare e modificare i valori delle variabili locali e globali nell'app in esecuzione.

- Visualizzare visualizzatori degli oggetti.

- Eseguire codice JavaScript all'interno del contesto di script corrente.

- Visualizzare errori ed eccezioni JavaScript, oltre alle eccezioni relative a Document Object Model (DOM) e Windows Runtime.

- Eseguire altre attività, come cancellare lo schermo. Per un elenco completo di comandi, vedi [JavaScript Console commands](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) .

> [!TIP]
> Se la finestra della console JavaScript è chiusa, **scegliere** >  **Debug Windows**  >  **console JavaScript** per ria aprirla. La finestra viene visualizzata solo durante una sessione di debug di script.

Usando la finestra Console JavaScript puoi interagire con la tua app senza arrestare e riavviare il debugger. Per altre informazioni, vedere [Aggiornare un'app (JavaScript).](../debugger/refresh-an-app-javascript.md) Per informazioni su altre funzionalità di debug JavaScript, ad esempio l'uso del DOM Explorer e l'impostazione dei punti di interruzione, vedere [Guida introduttiva:](../debugger/quickstart-debug-html-and-css.md) Eseguire il debug di app HTML e CSS e debug [in Visual Studio](debugging-windows-store-and-windows-universal-apps.md).

## <a name="debug-by-using-the-javascript-console-window"></a><a name="InteractiveConsole"></a> Eseguire il debug usando la finestra della console JavaScript
La procedura seguente consente di creare un'app `FlipView` e mostra come eseguire il debug interattivo di un errore di codifica JavaScript.

> [!NOTE]
> L'app di esempio è un'app UWP. Tuttavia, le funzioni della console descritte in questo articolo si applicano anche alle app create con Visual Studio Tools per Apache Cordova.

#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Per eseguire il debug di codice JavaScript nell'app FlipView

1. Creare una nuova soluzione in Visual Studio scegliendo **File**  >  **nuovo Project**.

2. Scegliere **JavaScript**  >  **Windows Universale,** quindi **scegliere App WinJS.**

3. Digitare un nome per il progetto, ad esempio `FlipViewApp`e scegliere **OK** per creare l'app.

4. Nell'elemento BODY di index.html sostituire il codice HTML esistente con questo codice:

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. Aprire default.css e aggiungere il codice CSS per il selettore `#fView` :

    ```css
    #fView {
        background-color:#0094ff;
        height: 500px;
        margin: 25px;
    }
    ```

6. Aprire default.js e sostituire il codice con il codice JavaScript seguente:

    ```javascript
    (function () {
        "use strict";

        var app = WinJS.Application;
        var activation = Windows.ApplicationModel.Activation;

        var myData = [];
        for (var x = 0; x < 4; x++) {
            myData[x] = { flipImg: "/images/logo.png" }
        };

        var pages = new WinJS.Binding.List(myData, { proxy: true });

        app.onactivated = function (args) {
            if (args.detail.kind === activation.ActivationKind.launch) {
                if (args.detail.previousExecutionState !==
                activation.ApplicationExecutionState.terminated) {
                    // TODO: . . .
                } else {
                    // TODO: . . .
                }
                args.setPromise(WinJS.UI.processAll());

                updateImages();
            }
        };

        function updateImages() {

            pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });

        };

        app.oncheckpoint = function (args) {
        };

        app.start();

        var publicMembers = {
            items: pages
        };

        WinJS.Namespace.define("Data", publicMembers);

    })();
    ```

7. Se non è già selezionata una destinazione di debug, scegliere **Computer** locale dall'elenco a discesa accanto al **pulsante Dispositivo** sulla barra degli **strumenti Debug:**

    ![Selezionare l'elenco di destinazione del debug](../debugger/media/js_select_target.png "JS_Select_Target")

8. Premere F5 per avviare il debugger.

    L'app viene eseguita, ma mancano le immagini. Gli errori APPHOST della finestra Console JavaScript indicano che mancano le immagini.

9. Con l'app in esecuzione, digitare il prompt di input della finestra della console (accanto al simbolo `FlipView` `Data.items` ">>" e premere INVIO.

    Nella finestra della console apparirà un visualizzatore per l'oggetto `items` . Questo indica che è stata creata un'istanza dell'oggetto `items` , che è disponibile nel contesto dello script corrente. Nella finestra della console è possibile fare clic sui nodi di un oggetto per visualizzare i valori delle proprietà (o usare i tasti di direzione). Come si può vedere nella figura, se si fa clic sull'oggetto `items._data` , i riferimenti relativi all'origine delle immagini non sono corretti, come previsto. Le immagini predefinite (logo.png) sono ancora presenti nell'oggetto e vi sono immagini mancanti frammiste alle immagini previste.

    ![Finestra della console JavaScript](../debugger/media/js_console_window.png "JS_Console_Window")

    Noterai anche che nell'oggetto `items._data` sono presenti molti più elementi del previsto.

10. Al prompt digitare `Data.items.push` e premere INVIO. Nella finestra della console viene visualizzato un visualizzatore per la funzione `push` , implementata in un file di progetto di [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] . In questa app, la funzione `push` viene usata per aggiungere gli elementi corretti. Con una piccola ricerca tramite IntelliSense, si scopre che sarebbe necessario usare `setAt` per sostituire le immagini predefinite.

11. Per risolvere il problema in modo interattivo senza interrompere la sessione di debug, aprire default.js e selezionare il codice seguente dalla funzione `updateImages` :

    ```javascript
    pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

     Copiare e incollare il codice nella richiesta di input della console JavaScript.

    > [!TIP]
    > Quando si incollano più righe di codice nella richiesta di input della finestra Console JavaScript, questa passa automaticamente alla modalità multiriga. È possibile premere CTRL+ALT+M per attivare e disattivare la modalità multiriga. Per eseguire uno script in modalità multiriga, premere CTRL+INVIO oppure scegliere il simbolo della freccia nell'angolo inferiore destro della finestra. Per altre informazioni, vedi [Modalità a riga singola e modalità multiriga nella finestra Console JavaScript](#SinglelineMultilineMode).

12. Correggi le chiamate di funzione `push` nella richiesta, sostituendo `pages.push` con `Data.items.setAt`. Il codice corretto dovrebbe essere analogo al seguente:

    ```javascript
    Data.items.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    Data.items.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    Data.items.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

    > [!TIP]
    > Se si desidera usare l'oggetto `pages` anziché `Data.items`, è necessario impostare un punto di interruzione nel codice per mantenere l'oggetto `pages` nell'ambito.

13. Scegliere il simbolo della freccia verde per eseguire lo script.

14. Premere CTRL+ALT+M per passare alla modalità a riga singola della richiesta di input della console e quindi scegliere Cancella **input** (la "X" rossa) per eliminare il codice dal prompt di input.

15. Digitare `Data.items.length = 3` al prompt, quindi premere INVIO. Verranno così rimossi gli elementi estranei dai dati.

16. Controllare di nuovo l'app e si noti che le immagini corrette sono nelle pagine `FlipView` corrette.

17. In DOM Explorer, è possibile visualizzare l'elemento DIV aggiornato e spostarsi nel sottoalbero per individuare gli elementi IMG previsti.

18. Arrestare il debug scegliendo **Debug**  >  **Arresta** debug o premendo MAIUSC+F5 e quindi correggere il codice sorgente.

    Per la pagina default.html completa contenente il codice di esempio corretto, vedere [Debug del codice di esempio HTML, CSS e JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md).

## <a name="interactive-debugging-and-break-mode"></a><a name="InteractiveDebuggingBreakMode"></a> Debug interattivo e modalità di interruzione
Quando si usano gli strumenti di debug JavaScript, come la finestra Console JavaScript, è possibile usare i punti di interruzione ed eseguire un'istruzione nel codice. Quando un programma in esecuzione nel debugger rileva un punto di interruzione, il debugger sospende temporaneamente l'esecuzione del programma. Quando l'esecuzione viene sospesa, il programma passa dalla modalità di esecuzione alla modalità di interruzione. È possibile riprendere l'esecuzione in qualsiasi momento.

Quando un programma è in modalità di interruzione, è possibile usare la finestra Console JavaScript per eseguire script e comandi validi nel contesto di esecuzione di script corrente. In questa procedura, si utilizzerà la versione corretta dell'app `FlipView` creata in precedenza per illustrare l'utilizzo della modalità di interruzione.

#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Per impostare un punto di interruzione ed eseguire il debug dell'app

1. Nel file default.html dell'app creata in precedenza aprire il menu di scelta rapida per la funzione e quindi scegliere Punto di interruzione Inserisci punto di `FlipView` `updateImages()`   >  **interruzione**.

2. Scegliere **Computer locale** nell'elenco a discesa accanto al **pulsante** Avvia debug sulla barra degli **strumenti Debug.**

3. Scegliere **Debug**  >  **Avvia debug** o premere F5.

    Quando l'esecuzione raggiunge la funzione `updateImages()` , l'app passa alla modalità di interruzione e la riga corrente dell'esecuzione del programma viene evidenziata in giallo.

    ![Uso della modalità di interruzione con la console JavaScript](../debugger/media/js_breakmode.png "JS_BreakMode")

    Puoi modificare i valori delle variabili in modo che abbiano immediatamente effetto sullo stato del programma senza terminare la sessione di debug corrente.

4. Digitare `updateImages` al prompt, quindi premere INVIO. Nella finestra della console apparirà un visualizzatore per la funzione.

5. Selezionare la funzione nella finestra della console per visualizzare l'implementazione della funzione.

    La figura seguente mostra la finestra della console in questa fase.

    ![Finestra della console JavaScript con un visualizzatore](../debugger/media/js_console_function_visualizer.png "JS_Console_Function_Visualizer")

6. Copia una riga della funzione dalla finestra di output alla richiesta di input e modifica il valore di indice in 3:

    ```javascript
    pages.setAt(3, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    ```

7. Premere INVIO per eseguire la riga di codice.

    Se si desidera eseguire il codice riga per riga, premere F11 oppure premere F5 per continuare l'esecuzione del programma.

8. Premere F5 per continuare l'esecuzione del programma. Verrà visualizzata l'app `FlipView` e tutte le quattro pagine mostrano ora una delle immagini non predefinite.

    Per tornare a Visual Studio, premere F12 o ALT+TAB.

## <a name="single-line-mode-and-multiline-mode-in-the-javascript-console-window"></a><a name="SinglelineMultilineMode"></a> Modalità a riga singola e modalità multiriga nella finestra Console JavaScript
La richiesta di input per la finestra Console JavaScript supporta sia la modalità a riga singola che la modalità multiriga. La procedura di debug interattivo riportata in questo argomento rappresenta un esempio di utilizzo di entrambe le modalità. È possibile premere CTRL+ALT+M per alternare le modalità.

La modalità a riga singola fornisce la cronologia dell'input. È possibile spostarsi nella cronologia dell'input usando i tasti freccia SU e freccia GIÙ. La modalità a riga singola cancella la richiesta di input quando si eseguono gli script. Per eseguire uno script in modalità a riga singola, premere INVIO.

La modalità multiriga non cancella la richiesta di input quando si eseguono gli script. Quando si passa alla modalità a riga singola dalla modalità multilinea, è possibile cancellare la riga di input premendo Cancella **input** (la "X" rossa). Per eseguire uno script in modalità multiriga, premere CTRL+INVIO oppure scegliere il simbolo della freccia nell'angolo inferiore destro della finestra.

## <a name="switching-the-script-execution-context"></a><a name="Switching"></a> Passaggio a un contesto di esecuzione di script diverso
La finestra Console JavaScript consente di interagire con un singolo contesto di esecuzione, che rappresenta una singola istanza dell'host della piattaforma web (WWAHost.exe), per volta. In alcuni scenari, l'app può avviare un'altra istanza dell'host, ad esempio quando si usa un `iframe`, un contratto di condivisione, un Web worker o un controllo `WebView` . Se è in esecuzione un'altra istanza dell'host, è possibile selezionare un contesto di esecuzione diverso durante l'esecuzione dell'app selezionando il contesto di esecuzione nell'elenco **Destinazione** .

La figura seguente mostra l'elenco Destinazione nella finestra Console JavaScript.

![Selezione della destinazione nella finestra della console JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")

Puoi anche cambiare il contesto di esecuzione usando il comando `cd` , ma devi ricordare il nome dell'altro contesto di esecuzione e il riferimento che usi deve essere incluso nell'ambito. L'elenco **Destinazione** offre un accesso migliore ad altri contesti di esecuzione.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di app in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [JavaScript Console commands](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)
- [Aggiornare un'applicazione (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [Tasti di scelta rapida](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017&preserve-view=true)
- [Debug del codice di esempio HTML, CSS e JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
- [Debug di un controllo WebView](../debugger/debug-a-webview-control.md)
- [Supporto tecnico e accessibilità](https://visualstudio.microsoft.com/vs/support/)
