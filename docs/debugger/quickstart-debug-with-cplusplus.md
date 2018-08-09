---
title: Eseguire il debug C++
description: Eseguire il debug di codice nativo usando il debugger di Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 036774134f705d95fbc526a9e6a336ac43005820
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639776"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Guida introduttiva: Eseguire il Debug con C++ con il debugger di Visual Studio

Il debugger di Visual Studio fornisce molte funzionalità potenti che consentono di eseguire il debug delle app. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

2. In **Visual C++** scegliere **Desktop di Windows** e nel riquadro al centro scegliere **Applicazione console di Windows**.

    Se non viene visualizzato il **applicazione Console di Windows** modello di progetto, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra il **nuovo progetto** nella finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **sviluppo di applicazioni Desktop con C++** carico di lavoro, quindi scegliere **Modify**.

3. Digitare un nome come **MyDbgApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

4. In MyDbgApp.cpp sostituire il codice seguente

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

Oggetto *punto di interruzione* è un marcatore che indica dove Visual Studio dovrebbe sospendere l'esecuzione di codice in modo che è possibile esaminare i valori delle variabili o il comportamento di memoria o se un ramo del codice di esecuzione. È la più semplice funzionalità di debug.

1. Per impostare il punto di interruzione, fare clic su nella barra di navigazione a sinistra del `doWork` chiamata di funzione (o selezionare la riga di codice e premere **F9**).

    ![Impostare un punto di interruzione](../debugger/media/dbg-qs-set-breakpoint.png "impostare un punto di interruzione")

2. A questo punto premere **F5** (oppure scegliere **Debug > Avvia debug**).

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint.png "raggiunge un punto di interruzione")

    Le pause di debugger in cui è impostato il punto di interruzione. L'istruzione in cui è in pausa l'esecuzione del debugger e l'app è indicato dalla freccia gialla. La riga con il `doWork` chiamata di funzione non è stata ancora eseguita.

    > [!TIP]
    > Se si dispone di un punto di interruzione in una ricorsione o un ciclo, o se si hanno molti punti di interruzione che spesso un'istruzione alla volta, usare una [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per assicurarsi che il codice venga sospeso solo quando vengono soddisfatte specifiche condizioni. Un punto di interruzione condizionale consente di risparmiare tempo e può anche rendere più semplice eseguire il debug di problemi che sono difficili da riprodurre.

    Quando si tenta di eseguire il debug degli errori correlati alla memoria in C++, è possibile usare anche i punti di interruzione per controllare i valori di indirizzo (cercare NULL) e i conteggi di riferimento. 

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger per continuare. Viene illustrato un comando di spostamento di codice utile che è stata introdotta in Visual Studio 2017.

Durante la pausa nel punto di interruzione, passare il mouse tramite l'istruzione `c1.push_back(20)` fino al verde **esecuzione fare clic su** pulsante ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata e quindi premere i **Fare clic su Esegui** pulsante.

![Esecuzione di fare clic su](../debugger/media/dbg-qs-run-to-click.png "esecuzione fare clic su")

L'app continua l'esecuzione, la chiamata a `doWork`e si posiziona sulla riga di codice in cui si fa clic sul pulsante.

Comandi della tastiera comuni usati per eseguire il codice includono **F10** e **F11**. Per altre istruzioni dettagliate, vedere la [Guida per principianti](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Esaminare le variabili in un suggerimento dati

1. Nella riga corrente del codice (contrassegnati con il puntatore di esecuzione giallo), passare il mouse su di `c1` oggetto con il mouse per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip.png "consente di visualizzare un suggerimento dati")

    Il suggerimento dati mostra il valore corrente del `c1` variabile e consente di controllare le relative proprietà. Durante il debug, se viene visualizzato un valore che non previsto, è probabile che sia un bug nelle righe di codice precedenti o chiamate. 

2. Espandere il suggerimento dati per esaminare i valori correnti delle proprietà di `c1` oggetto.

3. Se si vuole bloccare il suggerimento dati in modo che è possibile continuare a visualizzare il valore di `c1` mentre si esegue codice, fare clic sull'icona della puntina di piccole dimensioni. (È possibile spostare il suggerimento dati bloccato nel percorso desiderato).

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se si identifica una modifica che si desidera testare nel codice mentre è in corso una sessione di debug, è possibile farlo, troppo.

1. Scegliere la seconda istanza di `c2.front()` e cambiare `c2.front()` a `c2.back()`.

2. Premere **F10** (o **Debug > Esegui istruzione/routine**) alcune volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue.gif "modifica e continuazione")

    **F10** sposta in avanti l'istruzione del debugger uno alla volta, ma i passaggi su funzioni anziché eseguire un'istruzione in tali (ancora viene eseguito il codice che si ignora).

Per altre informazioni sull'uso di modifica e continuazione e sulle limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger oltre a collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
