---
title: Modifica di test codificati dell'interfaccia utente
description: Informazioni su come usare l'Editor test codificati dell'interfaccia utente per individuare, visualizzare e modificare i metodi di test e le azioni dell'interfaccia utente. Usare la mappa dei controlli dell'interfaccia utente per visualizzare e modificare i controlli corrispondenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 6be42c91936da9a02c735ea8759e6ccba918b4f12f7dc52a3cfdd9036fa793ff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441447"
---
# <a name="edit-coded-ui-tests-using-the-coded-ui-test-editor"></a>Modificare test codificati dell'interfaccia utente usando l'editor di test codificati dell'interfaccia utente

L'Editor di test codificati dell'interfaccia utente consente di modificare facilmente i test. Con l'Editor di test codificati dell'interfaccia utente è possibile individuare, visualizzare e modificare le proprietà dei metodi di test e delle azioni dell'interfaccia utente. Inoltre, è possibile usare la mappa del controllo dell'interfaccia utente per visualizzare e modificare i corrispondenti controlli.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisiti**

- Visual Studio Enterprise
- Componente Test codificato dell'interfaccia utente

## <a name="features-of-the-coded-ui-test-editor"></a>Funzionalità dell'editor di test codificati dell'interfaccia utente

Usare l'Editor di test codificati dell'interfaccia utente è più rapido ed efficiente che modificare il codice nei metodi di test codificato dell'interfaccia utente con l'editor del codice. Con l'Editor di test codificati dell'interfaccia utente, è possibile usare la barra degli strumenti e i menu di scelta rapida per individuare rapidamente e modificare i valori delle proprietà associati a controlli e azioni dell'interfaccia utente. Ad esempio, è possibile usare la barra degli strumenti dell'editor di test codificati dell'interfaccia utente per eseguire i comandi seguenti:

![Editor test interfaccia utente](../test/media/uitesteditor.png)

1. [Trova](../ide/finding-and-replacing-text.md) consente di individuare controlli e azioni dell'interfaccia utente.

2. **Elimina** rimuove le azioni dell'interfaccia utente indesiderate.

3. **Rinomina** modifica i nomi di controlli e metodi di test.

4. **Proprietà** apre la finestra **Proprietà** per l'elemento selezionato.

5. **Suddividi in nuovo metodo** consente di modularizzare le azioni dell'interfaccia utente.

6. **Sposta codice** aggiunge codice personalizzato ai metodi di test.

7. **Inserisci ritardo prima** aggiunge una pausa prima di un'azione dell'interfaccia utente, specificata in millisecondi.

8. **Individua controllo dell'interfaccia utente** identifica la posizione del controllo nell'interfaccia utente dell'applicazione sottoposta a test.

9. **Individua tutto** consente di verificare la proprietà del controllo e le modifiche significative ai controlli dell'applicazione.

Quando si apre il file *UIMap.uitest* associato al test codificato dell'interfaccia utente, il test viene aperto in **Editor di test codificati dell'interfaccia utente**. Le procedure seguenti descrivono come sia quindi possibile individuare e modificare i metodi di test e le proprietà per i controlli e le azioni dell'interfaccia utente usando la barra degli strumenti e i menu di scelta rapida dell'editor.

## <a name="open-a-coded-ui-test"></a>Aprire un test codificato dell'interfaccia utente

È possibile visualizzare e modificare il test codificato dell'interfaccia utente basato su Visual C# e Visual Basic usando l'**Editor di test codificati dell'interfaccia utente**.

![Modifica del menu di scelta rapida con il generatore di test codificati dell'interfaccia utente.](../test/media/editcodeduitest.png)

In **Esplora soluzioni** aprire il menu di scelta rapida *per UIMap.uitest* e scegliere **Apri**. Il test codificato dell'interfaccia utente viene visualizzato **nell'Editor test codificati dell'interfaccia utente.** Ora è possibile visualizzare e modificare i metodi registrati, i le azioni e i corrispondenti controlli nel test codificato dell'interfaccia utente.

> [!TIP]
> Quando si seleziona un'azione dell'interfaccia utente che si trova in un metodo nel riquadro **Azioni dell'interfaccia utente** , viene evidenziato il controllo corrispondente. È possibile modificare anche le proprietà delle azioni dell'interfaccia utente o dei controlli.

## <a name="modify-ui-action-and-control-properties"></a>Modificare le proprietà di azione e controllo dell'interfaccia utente

Usando l'Editor di test codificati dell'interfaccia utente, è possibile individuare rapidamente e visualizzare tutte le azioni dell'interfaccia utente nei metodi di test. Quando si seleziona l'azione dell'interfaccia utente nell'editor, il controllo corrispondente viene automaticamente evidenziato. Analogamente, se si seleziona un controllo, vengono evidenziate le azioni dell'interfaccia utente associate. Quando si seleziona un'azione dell'interfaccia utente o  un controllo, è quindi facile usare la finestra Proprietà per modificare le proprietà corrispondenti.

![Proprietà di un'azione dell'interfaccia utente](../test/media/codeduiedituiaction.png)

Per modificare le proprietà di un'azione dell'interfaccia utente, nel riquadro **Azioni dell'interfaccia utente** espandere il metodo di test contenente un'azione dell'interfaccia utente di cui si vogliono modificare le proprietà, selezionare l'azione dell'interfaccia utente e quindi modificare le proprietà usando la finestra Proprietà.

Ad esempio, se un server non è disponibile e al Web browser è associata un'azione dell'interfaccia utente che indica Vai alla pagina **Web http: \/ /Contoso1/default.aspx,** è possibile modificare l'URL in `http://Contoso2/default.aspx` .

![Proprietà del controllo](../test/media/codeduitestcontrolprop.png)

La modifica delle proprietà di un controllo è come quella delle azioni dell'interfaccia utente. Nel riquadro **Mappa dei controlli dell'interfaccia** utente selezionare il controllo da modificare e modificarne le proprietà usando la **finestra** Proprietà.

Ad esempio, uno sviluppatore potrebbe avere cambiato la proprietà **(ID)** in un pulsante nel codice sorgente dell'applicazione di cui è in corso il test da "idSubmit" a "idLogin". Con la proprietà **(ID)** modificata nell'applicazione, il test codificato dell'interfaccia utente non potrà individuare il pulsante e avrà esito negativo. In questo caso, il tester può aprire la raccolta **Proprietà di ricerca** e modificare la proprietà **Id** in modo che corrisponda al nuovo valore usato dallo sviluppatore nell'applicazione. Il tester potrebbe anche cambiare la proprietà **Nome descrittivo** da "Invia" ad "Accesso". Con questa modifica, l'azione dell'interfaccia utente associata nell'editor di test codificati dell'interfaccia utente viene aggiornata da "Scegli pulsante Invia" a "Scegli pulsante Accesso".

Dopo aver completato le modifiche, salvare le modifiche nel  file *UIMap.Designer* scegliendo Salva sulla barra Visual Studio strumenti.

### <a name="tips"></a>Suggerimenti

- Se la finestra **Proprietà** non viene visualizzata, tenere premuto **ALT** mentre si preme **INVIO** o, in alternativa, premere **F4**.

- Per annullare le modifiche apportate alle proprietà, **scegliere** Annulla **dal** menu Modifica o premere **CTRL** + **Z.**

- È possibile usare il **pulsante Trova sulla barra degli** strumenti dell'editor test codificati dell'interfaccia utente per aprire lo strumento Trova e sostituisci in Visual Studio.  È quindi possibile usare il **controllo Trova** per individuare un'azione dell'interfaccia utente nell'editor test codificato dell'interfaccia utente. Ad esempio, è possibile provare a cercare "Fare clic sul pulsante Accesso". Questo è utile nei test di grandi dimensioni. Non è possibile usare la funzionalità di sostituzione nello strumento **Trova e** sostituisci nell'Editor test codificati dell'interfaccia utente. Per altre informazioni, vedere la sezione relativa al controllo di ricerca in [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md).

- A volte può essere difficile identificare la posizione dei controlli nell'interfaccia utente dell'applicazione sottoposta a test. Una delle funzionalità dell'Editor di test codificati dell'interfaccia utente consente di selezionare un controllo elencato nella mappa del controllo dell'interfaccia utente e visualizzarne la posizione nell'applicazione sottoposta a test. Per altre informazioni, vedere [Individuare un controllo dell'interfaccia utente nell'applicazione sottoposta a test](#locate-a-ui-control-in-the-application-under-test) più avanti in questo articolo.

- Potrebbe essere necessario espandere il controllo contenitore che comprende il controllo che si vuole modificare. Per altre informazioni, vedere [Individuare un controllo e i relativi discendenti](#locate-a-control-and-its-descendants) più avanti nell'articolo.

## <a name="delete-unwanted-ui-actions"></a>Eliminare le azioni dell'interfaccia utente indesiderate

È possibile rimuovere facilmente le azioni indesiderate dell'interfaccia utente nel test codificato dell'interfaccia utente.

![Eliminazione di un'azione dell'interfaccia utente](../test/media/codeduideleteuiaction.png)

Nel riquadro **Azioni dell'interfaccia utente** espandere il metodo di test contenente l'azione dell'interfaccia utente che si vuole eliminare. Aprire il menu di scelta rapida per l'azione dell'interfaccia utente e scegliere **Elimina**.

## <a name="split-a-test-method-into-two-separate-methods"></a>Suddividere un metodo di test in due metodi distinti

È possibile suddividere un metodo di test per perfezionare o per modularizzare le azioni dell'interfaccia utente. Ad esempio, il test potrebbe disporre di un solo metodo di test con azioni dell'interfaccia utente in due controlli contenitore. La modularizzazione delle azioni dell'interfaccia utente può essere ottimizzata con due metodi corrispondenti a un solo contenitore.

![Dividere un metodo di test](../test/media/codeduitestsplitmethod1.png)

![Due metodi di test](../test/media/codeduitestsplitmethod2.png)

Nel riquadro **Azioni dell'interfaccia utente** espandere il metodo di test che si vuole suddividere in due metodi distinti e selezionare l'azione dell'interfaccia utente con cui far iniziare il nuovo metodo di test. Aprire il menu di scelta rapida per l'azione dell'interfaccia utente e quindi scegliere **Suddividi in nuovo metodo** scegliere il pulsante **Suddividi in nuovo metodo** sulla barra degli strumenti dell'Editor di test codificati dell'interfaccia utente. Il nuovo metodo di test viene visualizzato nel riquadro **Azioni dell'interfaccia** utente. che contiene le azioni dell'interfaccia utente a iniziare dall'azione in cui è stata specificata la suddivisione.

Al termine della suddivisione del metodo, salvare le modifiche nel  file *UIMap.Designer* scegliendo Salva sulla barra Visual Studio barra degli strumenti.

> [!WARNING]
> Se si suddivide un metodo, è necessario modificare qualsiasi codice che chiama il metodo esistente in modo che chiami anche il nuovo metodo che si sta per creare, se si vuole che queste azioni dell'interfaccia utente restino incluse. Quando si suddivide un metodo, verrà visualizzata una finestra di dialogo di Microsoft Visual Studio che avvisa che è necessario modificare qualsiasi codice chiami il metodo esistente in modo che chiami anche il nuovo metodo che si sta per creare. Scegliere **Sì**.

### <a name="tips"></a>Suggerimenti

- Per annullare la divisione, scegliere **Annulla** **dal** menu Modifica o premere **CTRL** + **Z.**

- È possibile rinominare il nuovo metodo. Selezionarlo nel riquadro **Azioni dell'interfaccia utente** e scegliere il **pulsante Rinomina** nella barra degli strumenti dell'editor test codificati dell'interfaccia utente.

   -oppure-

   Aprire il menu di scelta rapida per il nuovo metodo di test e scegliere **Rinomina**.

   Verrà visualizzata una finestra di dialogo di Microsoft Visual Studio che avvisa che è necessario modificare qualsiasi codice faccia riferimento al metodo. Scegliere **Sì**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a>Spostare un metodo di test nel file UIMap per facilitare la personalizzazione

Se si determina che uno dei metodi di test nel test codificato dell'interfaccia utente richiede codice personalizzato, è necessario spostarlo nel file *UIMap.cs* o *UIMap.vb.* In caso contrario, il codice verrà sovrascritto ogni volta che il test codificato dell'interfaccia utente verrà ricompilato. Se non si sposta il metodo, il codice personalizzato verrà sovrascritto ogni volta che il test verrà ricompilato.

Nel **riquadro** Azione dell'interfaccia utente selezionare il metodo di test che si vuole spostare nel file *UIMap.cs* o *UIMap.vb* per facilitare la funzionalità del codice personalizzato che non verrà sovrascritta quando il codice di test viene ricompilato. Scegliere poi il pulsante **Sposta codice** sulla barra degli strumenti dell'Editor di test codificati dell'interfaccia utente o aprire il menu di scelta rapida per il metodo di test e scegliere **Sposta codice**. Il metodo di test viene rimosso dal file *UIMap.uitest* e non viene più visualizzato nel riquadro **Azioni dell'interfaccia** utente. Per modificare il file di test spostato, aprire il file *UIMap.cs* o *UIMap.vb* **da Esplora soluzioni**.

Dopo aver modificato il metodo , salvare le modifiche apportate  al file *UIMap.Designer* scegliendo Salva sulla barra Visual Studio strumenti.

> [!WARNING]
> Dopo aver spostato un metodo, non è più possibile modificarlo mediante l'editor di test codificati dell'interfaccia utente. È necessario aggiungere il codice personalizzato e gestirlo usando l'editor del codice. Quando si sposta un metodo, verrà visualizzata una finestra di dialogo di Microsoft Visual Studio Avvisa che il metodo verrà spostato dal file *UIMap.uitest* al file *UIMap.cs* o *UIMap.vb* e che non sarà più possibile modificare il metodo usando l'Editor di test codificati dell'interfaccia utente. Scegliere **Sì**.

### <a name="tips"></a>Suggerimenti

Per annullare lo spostamento, scegliere **Annulla** **dal** menu Modifica o premere **CTRL** + **Z.** È tuttavia necessario rimuovere manualmente il codice dal file *UIMap.cs* o *UIMap.vb.*

## <a name="locate-a-ui-control-in-the-application-under-test"></a>Individuare un controllo dell'interfaccia utente nell'applicazione sottoposta a test

A volte può essere difficile identificare la posizione dei controlli nell'interfaccia utente dell'applicazione sottoposta a test. Una delle funzionalità dell'Editor di test codificati dell'interfaccia utente consente di selezionare un controllo elencato nella mappa del controllo dell'interfaccia utente e visualizzarne la posizione nell'applicazione sottoposta a test. La funzionalità **Individua controllo dell'interfaccia utente** nell'applicazione sottoposta a test consente anche di verificare le modifiche delle proprietà di ricerca apportate a un controllo.

![Individuazione di un controllo dell'interfaccia utente](../test/media/codeduilocatecontrol.png)

![Controllo individuato in un'applicazione in fase di test](../test/media/codeduilocatecontrol2.png)

Nel riquadro **Mappa del controllo dell'interfaccia utente** selezionare il controllo che si vuole individuare nell'applicazione associata al test. Aprire quindi il menu di scelta rapida per il controllo e quindi scegliere **Individua controllo dell'interfaccia utente**. Nell'applicazione di cui è in corso il test, il controllo viene identificato da un bordo blu.

> [!NOTE]
> Prima di individuare un controllo dell'interfaccia utente, verificare che l'applicazione associata al test sia in esecuzione.

### <a name="tips"></a>Suggerimenti

È possibile usare l'opzione **Individua tutto** per verificare che tutti i controlli in un contenitore vengano individuati correttamente. Questa opzione viene descritta nella sezione successiva.

## <a name="locate-a-control-and-its-descendants"></a>Individuare un controllo e i relativi discendenti

È possibile verificare che tutti i controlli in un contenitore possano essere individuati correttamente nell'interfaccia utente dell'applicazione sottoposta a test. Può essere utile per la verifica delle eventuali modifiche delle proprietà di ricerca apportate nel contenitore. Inoltre, se sono state apportate modifiche considerevoli nell'interfaccia utente dell'applicazione sottoposta a test, è possibile verificare che le proprietà di ricerca del controllo esistenti siano ancora corrette.

![Individuazione di tutti i controlli discendenti](../test/media/codeduilocateall.png)

![Tutti i controlli individuati](../test/media/codeduilocateall2.png)

Nel riquadro **Mappa del controllo dell'interfaccia utente** selezionare il controllo contenitore da individuare e per cui visualizzare tutti i discendenti. Aprire quindi il menu di scelta rapida per il controllo e scegliere **Individua tutto**. Il controllo contenitore e tutti i controlli discendenti vengono contrassegnati nell'editor di test codificati dell'interfaccia utente con un segno di spunta verde o una "X" rossa. Questi contrassegni consentono di sapere se i controlli sono stati individuati nell'applicazione sottoposta a test.

> [!NOTE]
> Prima di individuare i controlli dell'interfaccia utente, verificare che l'applicazione associata al test sia in esecuzione.

## <a name="insert-a-delay-before-a-ui-action"></a>Inserire un ritardo prima di un'azione dell'interfaccia utente

Talvolta, potrebbe essere necessario fare in modo che il test attenda che si verifichino determinati eventi, ad esempio che venga visualizzata una finestra, venga nascosto l'indicatore di stato e così via. Usando l'Editor di test codificati dell'interfaccia utente, è possibile inserire un ritardo prima di un'azione dell'interfaccia utente per raggiungere questo risultato. È possibile specificare il numero di secondi di ritardo desiderati.

![Inserimento di un ritardo prima di un'azione dell'interfaccia utente](../test/media/codeduidelay.png)

![Ritardo aggiunto con 5 secondi](../test/media/codeduidealy2.png)

Nel riquadro **Azioni dell'interfaccia utente** espandere il metodo di test contenente l'azione dell'interfaccia utente prima della quale si vuole inserire un ritardo. Selezionare l'azione dell'interfaccia utente. Aprire quindi il menu di scelta rapida per l'azione dell'interfaccia utente e scegliere **Inserisci ritardo prima**. Un ritardo viene inserito ed evidenziato prima dell'azione dell'interfaccia utente selezionata con il testo seguente: **Attendere 1 secondo per ritardo utente tra azioni**. Nella finestra **Proprietà** modificare il valore della proprietà **Delay** sul numero di millisecondi desiderato.

Al termine dell'inserimento del ritardo, salvare le modifiche apportate al file *UIMap.Designer* scegliendo **Salva** sulla barra Visual Studio barra degli strumenti.

Se è necessario assicurarsi che un controllo specifico sia disponibile prima di un'azione dell'interfaccia utente, è consigliabile aggiungere il codice personalizzato al metodo di test usando il metodo UITestControl.WaitForControlXXX() appropriato. Per altre informazioni, vedere Esecuzione [di test codificati dell'interfaccia utente in attesa di eventi specifici durante la riproduzione.](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)

## <a name="see-also"></a>Vedi anche

- [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md)
- [Creare test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md)
- [Creare un test codificato dell'interfaccia utente basato sui dati](../test/creating-a-data-driven-coded-ui-test.md)
- [Procedura dettagliata: Creazione, modifica e gestione di un test codificato dell'interfaccia utente](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
