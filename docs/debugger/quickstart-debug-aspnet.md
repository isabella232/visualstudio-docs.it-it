---
title: Eseguire il debug ASP.NET Core
description: Eseguire ASP.NET Core debug usando il debugger Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 8f4455a8cfcbc62cc06e48692a2d19b55d1686bf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065293"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Guida introduttiva: Eseguire il ASP.NET Core debug con il debugger Visual Studio debug

Il debugger di Visual Studio propone molte funzionalità potenti per il debug delle app. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

1. Aprire Visual Studio.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **asp.net**, scegliere **Modelli**, quindi scegliere **Crea una nuova applicazione Web ASP.NET Core**. Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **Project**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** in **Visual C#** scegliere **Web** e quindi nel riquadro centrale scegliere **Applicazione Web ASP.NET Core**. Digitare un nome come **MyDbgApp** e fare clic su **OK**.

    Nella finestra di dialogo visualizzata scegliere **Applicazione Web** nel riquadro centrale e quindi fare clic su **OK**.

    ![Scegliere un'applicazione Web](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Se il modello di progetto **Applicazione Web ASP.NET Core** non viene visualizzato, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, aprendo così il programma di installazione Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.

    Visual Studio crea il progetto.

1. In Esplora soluzioni aprire About.cshtml.cs (sotto Pages/About.cshtml) e sostituire il codice seguente

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    Con questo:

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

Un *punto di interruzione* è un indicatore che segnala il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. È la più semplice funzionalità di debug.

1. Per impostare il punto di interruzione, fare clic nella barra di navigazione a sinistra della funzione `doWork` o selezionare la riga di codice e premere **F9**.

    ![Imposta punto di interruzione](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Il punto di interruzione è impostato a sinistra della parentesi graffa di apertura (`{`).

1. Premere **F5** o scegliere **Debug > Avvia debug**.

1. Quando viene caricata la pagina Web, fare clic sul collegamento **Informazioni** nella parte superiore della pagina web.

    Il debugger si ferma in corrispondenza del punto di interruzione impostato. L'istruzione in corrispondenza della quale si è bloccato il debugger e si è interrotta l'esecuzione dell'app è indicata dalla freccia gialla. La riga con la parentesi graffa di apertura (`{`) dopo la dichiarazione di funzione `doWork` non è stata ancora eseguita.

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Se è presente un punto di interruzione in un ciclo o in una ricorsione oppure sono presenti molti punti di interruzione in un codice che si esegue di frequente, usare un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per fare in modo che il codice venga sospeso SOLO se sono soddisfatte specifiche condizioni. Un punto di interruzione condizionale consente di risparmiare tempo e può facilitare il debug di problemi che sono difficili da riprodurre.

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger di continuare. Viene illustrato un utile comando di esplorazione del codice disponibile a partire da Visual Studio 2017.

Mentre l'elaborazione è ferma al punto di interruzione, passare il mouse sopra l'istruzione `return c2` finché appare il pulsante verde **Esegui fino alla riga selezionata**![Esegui fino alla riga selezionata](../debugger/media/dbg-tour-run-to-click.png) quindi premere il pulsante **Esegui fino alla riga selezionata**.

![Esegui fino alla riga selezionata](../debugger/media/dbg-qs-run-to-click-aspnet.png)

L'app riprende l'esecuzione e si blocca sulla riga di codice in cui si è fatto clic.

I comandi della tastiera comuni usati per eseguire il codice sono **F10** e **F11**. Per altre istruzioni dettagliate, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Esaminare le variabili in un suggerimento dati

1. Nella riga corrente del codice, segnalata dal puntatore di esecuzione giallo, passare il mouse sopra l'oggetto `c2` per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Il suggerimento dati mostra il valore corrente della variabile `c2` e consente di controllarne le proprietà. Se viene visualizzato un valore non previsto durante il debug, è probabile che ci sia un bug nelle righe di codice precedenti o chiamate.

2. Espandere il suggerimento dati per esaminare i valori delle proprietà dell'oggetto `c2`.

3. Se si preferisce bloccare il suggerimento dati in modo che sia sempre possibile vedere il valore di `c2` mentre si esegue il codice, fare clic sulla piccola icona Aggiungi. Il suggerimento dati aggiunto può essere spostato in una posizione più comoda.

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se durante una sessione di debug, nel codice si rileva una modifica che si desidera testare, è possibile farlo.

1. Nel metodo `OnGet` fare clic sulla seconda istanza di `result.First.Value` e modificare `result.First.Value` in `result.Last.Value`.

1. Premere **F10** (o selezionare **Debug > Esegui istruzione/routine**) alcune volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Modifica e continuazione")

    **F10** fa avanzare il debugger un'istruzione alla volta, ma ignora le funzioni anziché fermarsi. Il codice ignorato viene comunque eseguito.

Per altre informazioni sull'uso della funzione di modifica e continua e sulle limitazioni della funzionalità, vedere [Modificare il codice e continuare il debug](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
