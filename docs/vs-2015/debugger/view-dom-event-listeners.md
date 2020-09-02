---
title: Visualizzare i listener di eventi DOM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693580"
---
# <a name="view-dom-event-listeners"></a>Visualizzare i listener di eventi DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image windows_and_phone_content.png "windows_and_phone_content")

 La scheda **eventi** di Dom Explorer Mostra gli eventi associati a un elemento DOM. Ogni nodo principale nella scheda **eventi** rappresenta un evento con sottoscrittori attivi. Il nodo principale contiene i sottonodi che rappresentano i listener di eventi registrati per l'evento specifico. Oltre a visualizzare i listener di eventi, puoi usare questa scheda per spostarti nel percorso del listener di eventi nel codice JavaScript. Le informazioni contenute in questo argomento sono applicabili alle app di Windows Store compilate con HTML e JavaScript.

 L'elenco nella scheda **eventi** è dinamico. Se aggiungi un listener di eventi quando l'applicazione è in esecuzione, il nuovo listener verrà visualizzato nella scheda. Per informazioni sull'aggiunta e la rimozione di listener di eventi, vedere [Suggerimenti per la risoluzione dei problemi relativi ai listener di eventi](#Tips) in questo argomento.

> [!NOTE]
> I listener di eventi per gli elementi di codice che non sono elementi DOM, ad esempio `xhr` , non vengono visualizzati nella scheda **eventi** .

## <a name="view-event-listeners-for-dom-elements"></a>Visualizzare listener di eventi per elementi DOM
 Questo esempio mostra un'app di Windows Phone Store. Le funzionalità di DOM Explorer qui descritte sono supportate anche per le app di Windows Store.

#### <a name="to-view-event-listeners"></a>Per visualizzare i listener di eventi

1. In Visual Studio crea un'app JavaScript che usa il modello di progetto Applicazione pivot Windows Phone.

2. Con il modello aperto in Visual Studio, selezionare **Emulator 8,1 WVGA 4in 512MB** nell'elenco a discesa sulla barra degli strumenti debug nel debugger:

     ![Selezione di una destinazione per il debug](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Premi F5 per eseguire l'app in modalità debug.

4. Nell'app in esecuzione passare alla **sezione 3** elemento pivot.

5. Passa a Visual Studio (ALT+TAB o F12).

6. In DOM Explorer scegli `Find` nell'angolo superiore destro.

7. Digitare `ListView`e premere Invio.

8. Se necessario, scegliere il pulsante **Avanti** per trovare l' `DIV` elemento che rappresenta il `ListView` controllo (questo elemento ha un `data-win-control` valore di `WinJS.UI.ListView` ).

     L'elemento `DIV` dovrebbe ora essere selezionato in DOM Explorer.

9. Scegliere la scheda **eventi** nel riquadro sul lato destro del Dom Explorer.

     Ora puoi visualizzare gli eventi con sottoscrittori attivi per l'elemento `DIV`, come illustrato di seguito.

     ![Scheda Eventi di DOM Explorer](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Per individuare i listener per questi eventi, fai clic sui link dei file JavaScript associati.

11. Per identificare rapidamente i listener per gli elementi padre nella gerarchia DOM, scegli un elemento padre nell'elenco della gerarchia nella parte inferiore di DOM Explorer.

     ![Selezione degli elementi padre nella gerarchia DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     La scheda **eventi** Mostra i listener di eventi per qualsiasi elemento scelto nell'elenco gerarchia.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Suggerimenti per la risoluzione dei problemi relativi ai listener di eventi
 In alcuni scenari di app, i listener di eventi devono essere rimossi in modo esplicito tramite [RemoveEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Usare la scheda **eventi** nel DOM Explorer per verificare se i listener di eventi sono stati rimossi dagli elementi DOM durante l'esecuzione del codice. Ecco alcuni suggerimenti utili per risolvere questi tipi di problemi:

- Per le app che usano il modello di navigazione a pagina singola implementato nei [modelli di progetto](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)di Visual Studio, non è in genere necessario rimuovere i listener di eventi registrati per gli oggetti, ad esempio gli elementi DOM, che fanno parte di una pagina. In questo scenario, un elemento DOM e i listener di eventi associati hanno la stessa durata e possono essere sottoposti a Garbage Collection.

- Se la durata dell'oggetto o dell'elemento DOM è diversa da quella del listener di eventi associato, potrebbe essere necessario chiamare il metodo `removeEventListener`. Se, ad esempio, usi l'evento `window.onresize`, potresti dover rimuovere il listener di eventi se esci dalla pagina in cui gestisci l'evento.

- Se `removeEventListener` non riesce a rimuovere il listener specificato, potrebbe venire chiamato in un'istanza diversa dell'oggetto. È possibile usare il metodo [Bind (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) per risolvere questo problema quando si aggiunge il listener.

- Per rimuovere un listener di eventi aggiunto tramite il [metodo Bind (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) o utilizzando una funzione anonima, archiviare un'istanza della funzione quando si aggiunge il listener. Ecco un metodo per usare questo modello in modo sicuro:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Se usi il codice seguente invece di archiviare un riferimento alla funzione associata, non potrai rimuovere il listener di eventi in modo esplicito:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- Non puoi rimuovere un listener di eventi tramite `removeEventListener` se lo hai aggiunto usando l'attributo `obj.on<eventname>`, ad esempio `window.onresize = handlerFunc`.

- Usare JavaScript Memory Analyzer per la [memoria JavaScript](../profiling/javascript-memory.md) nell'app. I listener di eventi che devono essere rimossi in modo esplicito potrebbero venire rilevati come perdita di memoria.

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)
- [Eseguire il debug di stili CSS tramite DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md)
- [Eseguire il debug del layout usando DOM Explorer](../debugger/debug-layout-using-dom-explorer.md)