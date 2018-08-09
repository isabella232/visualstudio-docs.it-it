---
title: Debug di ASP.NET
description: Eseguire il debug ASP.NET usando il debugger di Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636987"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Guida introduttiva: Eseguire il Debug di ASP.NET con il debugger di Visual Studio

Il debugger di Visual Studio fornisce molte funzionalità potenti che consentono di eseguire il debug delle app. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

1. Sotto **Visual c#**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET Core**.

1. Digitare un nome come **MyDbgApp** e fare clic su **OK**.

1. Nella finestra di dialogo visualizzata, scegliere **applicazione Web** nel riquadro intermedio e quindi fare clic su **OK**.

     Se non viene visualizzato il **applicazione Web** modello di progetto, fare clic sui **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra il **nuovo progetto** nella finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

    ![Scegliere un'applicazione Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio crea il progetto.

1. In Esplora soluzioni aprire About.cshtml.cs (sotto cshtml) e sostituire il codice seguente

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    con questo codice:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

Oggetto *punto di interruzione* è un marcatore che indica dove Visual Studio dovrebbe sospendere l'esecuzione di codice in modo che è possibile esaminare i valori delle variabili o il comportamento di memoria o se un ramo del codice di esecuzione. È la più semplice funzionalità di debug.

1. Per impostare il punto di interruzione, fare clic su nella barra di navigazione a sinistra del `doWork` funzione (o selezionare la riga di codice e premere **F9**).

    ![Imposta punto di interruzione](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Il punto di interruzione è impostato a sinistra della parentesi graffa di apertura (`{`).

1. A questo punto premere **F5** (oppure scegliere **Debug > Avvia debug**).

1. Quando viene caricata la pagina web, scegliere il **sulle** collegamento nella parte superiore della pagina web.

    Le pause di debugger in cui è impostato il punto di interruzione. L'istruzione in cui è in pausa l'esecuzione del debugger e l'app è indicato dalla freccia gialla. La riga con la parentesi graffa aperta (`{`) dopo il `doWork` dichiarazione di funzione non è stata ancora eseguita.

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Se si dispone di un punto di interruzione in una ricorsione o un ciclo, o se si hanno molti punti di interruzione che spesso un'istruzione alla volta, usare una [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per assicurarsi che il codice venga sospeso solo quando vengono soddisfatte specifiche condizioni. Questo consente di risparmiare tempo e può anche rendere più semplice eseguire il debug di problemi che sono difficili da riprodurre.

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger per continuare. Viene illustrato un comando di spostamento di codice utile che è stata introdotta in Visual Studio 2017.

Durante la pausa nel punto di interruzione, passare il mouse tramite l'istruzione `return c2` fino al verde **esecuzione fare clic su** pulsante ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png) viene visualizzato e quindi premere il **esecuzione fare clic su** pulsante.

![Esecuzione di fare clic su](../debugger/media/dbg-qs-run-to-click-aspnet.png)

L'app continua l'esecuzione e si posiziona sulla riga di codice in cui si fa clic sul pulsante.

Comandi della tastiera comuni usati per eseguire il codice includono **F10** e **F11**. Per altre istruzioni dettagliate, vedere la [Guida per principianti](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Esaminare le variabili in un suggerimento dati

1. Nella riga corrente del codice (contrassegnati con il puntatore di esecuzione giallo), passare il mouse su di `c2` oggetto con il mouse per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Il suggerimento dati mostra il valore corrente del `c2` variabile e consente di controllare le relative proprietà. Durante il debug, se viene visualizzato un valore che non previsto, è probabile che sia un bug nelle righe di codice precedenti o chiamate. 

2. Espandere il suggerimento dati per esaminare i valori correnti delle proprietà di `c2` oggetto.

3. Se si vuole bloccare il suggerimento dati in modo che è possibile continuare a visualizzare il valore di `c2` mentre si esegue codice, fare clic sull'icona della puntina di piccole dimensioni. (È possibile spostare il suggerimento dati bloccato nel percorso desiderato).

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se si identifica una modifica che si desidera testare nel codice mentre è in corso una sessione di debug, è possibile farlo, troppo.

1. Nel `OnGet` metodo, scegliere la seconda istanza di `result.First.Value` e modificare `result.First.Value` a `result.Last.Value`.

1. Premere **F10** (o **Debug > Esegui istruzione/routine**) alcune volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "modifica e continuazione")

    **F10** sposta in avanti l'istruzione del debugger uno alla volta, ma i passaggi su funzioni anziché eseguire un'istruzione in tali (ancora viene eseguito il codice che si ignora).

Per altre informazioni sull'uso di modifica e continuazione e sulle limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger oltre a collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
