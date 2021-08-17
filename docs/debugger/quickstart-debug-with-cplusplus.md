---
title: Debug C++
description: Eseguire il debug del codice nativo usando il debugger di Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 0292e73f952a05652142b8e146d21915af73bde2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105028"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Guida introduttiva: eseguire il debug con C++ usando il debugger di Visual Studio

Il debugger di Visual Studio propone molte funzionalità potenti per il debug delle app. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

1. Aprire Visual Studio e creare un progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **c++**, scegliere **Modelli** e quindi scegliere **Create new Console App project** (Crea nuovo progetto app console). Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **Project**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** in **Visual C++** scegliere **Windows Desktop** e quindi nel riquadro centrale scegliere **Applicazione console di Windows**. Digitare quindi un nome come **MyDbgApp** e fare clic su **OK**.
    ::: moniker-end

    Se il modello di progetto **Applicazione console di Windows** non viene visualizzato, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, aprendo così il programma di installazione Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++**, quindi scegliere **Modifica**.

    Visual Studio crea il progetto.

1. In MyDbgApp.cpp sostituire il codice seguente

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con questo codice (non rimuovere `#include "stdafx.h"`):

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

Un *punto di interruzione* è un indicatore che segnala il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. È la più semplice funzionalità di debug.

1. Per impostare il punto di interruzione, fare clic nella barra di navigazione a sinistra della chiamata di funzione `doWork` o selezionare la riga di codice e premere **F9**.

    ![Impostare un punto di interruzione](../debugger/media/dbg-qs-set-breakpoint.png "Imposta punto di interruzione")

2. Premere **F5** o scegliere **Debug > Avvia debug**.

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint.png "Raggiungere un punto di interruzione")

    Il debugger si ferma in corrispondenza del punto di interruzione impostato. L'istruzione in corrispondenza della quale si è bloccato il debugger e si è interrotta l'esecuzione dell'app è indicata dalla freccia gialla. La riga con la chiamata di funzione `doWork` non è stata ancora eseguita.

    > [!TIP]
    > Se è presente un punto di interruzione in un ciclo o in una ricorsione oppure sono presenti molti punti di interruzione in un codice che si esegue di frequente, usare un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per fare in modo che il codice venga sospeso SOLO se sono soddisfatte specifiche condizioni. Un punto di interruzione condizionale consente di risparmiare tempo e può facilitare il debug di problemi che sono difficili da riprodurre.

    Quando si tenta di eseguire il debug degli errori di memoria in C++, i punti di interruzione possono anche servire per controllare i valori degli indirizzo (cercare NULL) e i conteggi di riferimento.

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger di continuare. Viene illustrato un utile comando di esplorazione del codice disponibile a partire da Visual Studio 2017.

Mentre l'elaborazione è ferma al punto di interruzione, passare il mouse sopra l'istruzione `c1.push_back(20)` finché appare il pulsante verde **Esegui fino alla riga selezionata**![Esegui fino alla riga selezionata](../debugger/media/dbg-tour-run-to-click.png "RunToClick") quindi premere il pulsante **Esegui fino alla riga selezionata**.

![Esegui per fare clic su](../debugger/media/dbg-qs-run-to-click.png "Esegui fino alla riga selezionata")

L'app riprende l'esecuzione, esegue la chiamata a `doWork` e si blocca sulla riga di codice in cui si è fatto clic.

I comandi della tastiera comuni usati per eseguire il codice sono **F10** e **F11**. Per altre istruzioni dettagliate, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Esaminare le variabili in un suggerimento dati

1. Nella riga corrente del codice, segnalata dal puntatore di esecuzione giallo, passare il mouse sopra l'oggetto `c1` per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip.png "Visualizzare un suggerimento dati")

    Il suggerimento dati mostra il valore corrente della variabile `c1` e consente di controllarne le proprietà. Se viene visualizzato un valore non previsto durante il debug, è probabile che ci sia un bug nelle righe di codice precedenti o chiamate.

2. Espandere il suggerimento dati per esaminare i valori delle proprietà dell'oggetto `c1`.

3. Se si preferisce bloccare il suggerimento dati in modo che sia sempre possibile vedere il valore di `c1` mentre si esegue il codice, fare clic sulla piccola icona Aggiungi. Il suggerimento dati aggiunto può essere spostato in una posizione più comoda.

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se durante una sessione di debug, nel codice si rileva una modifica che si desidera testare, è possibile farlo.

1. Fare clic sulla seconda istanza di `c2.front()` e modificare `c2.front()` in `c2.back()`.

2. Premere **F10** (o selezionare **Debug > Esegui istruzione/routine**) alcune volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue.gif "Modifica e continuazione")

    **F10** fa avanzare il debugger un'istruzione alla volta, ma ignora le funzioni anziché fermarsi. Il codice ignorato viene comunque eseguito.

Per altre informazioni sull'uso della funzione di modifica e continua e sulle limitazioni della funzionalità, vedere [Modificare il codice e continuare il debug](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
