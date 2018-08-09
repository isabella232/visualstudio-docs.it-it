---
title: Eseguire il debug di codice gestito | Microsoft Docs
description: Eseguire il debug in c# o Visual Basic usando il debugger di Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ba06156a8fa44a61b489deba6104673e8fb08ce
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637523"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Guida introduttiva: Eseguire il Debug con codice gestito utilizzando il debugger di Visual Studio

Il debugger di Visual Studio fornisce molte funzionalità potenti che consentono di eseguire il debug delle app. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base.

## <a name="create-a-new-project"></a>Creare un nuovo progetto 

1. In Visual Studio scegliere **File > Nuovo progetto**.

2. Sotto **Visual c#** oppure **Visual Basic**, scegliere **.NET Core**, quindi nel riquadro centrale scegliere **App Console (.NET Core)**.

     Se non viene visualizzato il modello di progetto **Console App (.NET Core)** (App console (.NET Core)), fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **sviluppo di applicazioni desktop .NET** e **.NET Core** carico di lavoro, quindi scegliere **Modify**.

3. Digitare un nome come **MyDbgApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

4. Nelle *Program.cs* oppure *Module1.vb*, sostituire il codice seguente

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    con questo codice:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > In Visual Basic verificare che l'oggetto di avvio sia impostato su `Sub Main` (**Proprietà > Applicazione > Oggetto di avvio**).

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

Oggetto *punto di interruzione* è un marcatore che indica dove Visual Studio dovrebbe sospendere l'esecuzione di codice in modo che è possibile esaminare i valori delle variabili o il comportamento di memoria o se un ramo del codice di esecuzione. È la più semplice funzionalità di debug.

1. Per impostare il punto di interruzione, fare clic su nella barra di navigazione a sinistra del `doWork` chiamata di funzione (o selezionare la riga di codice e premere **F9**).

    ![Impostare un punto di interruzione](../debugger/media/dbg-qs-set-breakpoint-csharp.png "impostare un punto di interruzione")

2. A questo punto premere **F5** (oppure scegliere **Debug > Avvia debug**).

    ![Raggiungere un punto di interruzione](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "raggiunge un punto di interruzione")

    Le pause di debugger in cui è impostato il punto di interruzione. L'istruzione in cui è in pausa l'esecuzione del debugger e l'app è indicato dalla freccia gialla. La riga con il `doWork` chiamata di funzione non ha ancora eseguito.

    > [!TIP]
    > Se si dispone di un punto di interruzione in una ricorsione o un ciclo, o se si hanno molti punti di interruzione che spesso un'istruzione alla volta, usare una [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) per assicurarsi che il codice venga sospeso solo quando vengono soddisfatte specifiche condizioni. Un punto di interruzione condizionale consente di risparmiare tempo e può anche risultare più semplice eseguire il debug di problemi che sono difficili da riprodurre.

## <a name="navigate-code"></a>Spostarsi all'interno del codice

Sono disponibili diversi comandi per indicare al debugger per continuare. Viene illustrato un comando di spostamento di codice utile che è stata introdotta in Visual Studio 2017.

Durante la pausa nel punto di interruzione, passare il mouse tramite l'istruzione `c1.AddLast(20)` fino al verde **esecuzione fare clic su** pulsante ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata e quindi premere i **Fare clic su Esegui** pulsante.

![Esecuzione di fare clic su](../debugger/media/dbg-qs-run-to-click-csharp.png "esecuzione fare clic su")

L'app continua l'esecuzione, la chiamata a `doWork`e si posiziona sulla riga di codice in cui si fa clic sul pulsante.

Comandi della tastiera comuni usati per eseguire il codice includono **F10** e **F11**. Per altre istruzioni dettagliate, vedere la [Guida per principianti](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Esaminare le variabili in un suggerimento dati

1. Nella riga corrente del codice (contrassegnati con il puntatore di esecuzione giallo), passare il mouse su di `c1` oggetto con il mouse per visualizzare un suggerimento dati.

    ![Visualizzare un suggerimento dati](../debugger/media/dbg-qs-data-tip-csharp.png "consente di visualizzare un suggerimento dati")

    Il suggerimento dati mostra il valore corrente del `c1` variabile e consente di controllare le relative proprietà. Durante il debug, se viene visualizzato un valore che non previsto, è probabile che sia un bug nelle righe di codice precedenti o chiamate. 

2. Espandere il suggerimento dati per esaminare i valori correnti delle proprietà di `c1` oggetto.

3. Se si vuole bloccare il suggerimento dati in modo che è possibile continuare a visualizzare il valore di `c1` mentre si esegue codice, fare clic sull'icona della puntina di piccole dimensioni. (È possibile spostare il suggerimento dati bloccato nel percorso desiderato).

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

Se si identifica una modifica che si desidera testare nel codice mentre è in corso una sessione di debug, è possibile farlo, troppo.

1. Scegliere la seconda istanza di `c2.First.Value` e cambiare `c2.First.Value` a `c2.Last.Value`.

2. Premere **F10** (o **Debug > Esegui istruzione/routine**) alcune volte per far avanzare il debugger ed eseguire il codice modificato.

    ![Modifica e continuazione](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "modifica e continuazione")

    **F10** sposta in avanti l'istruzione del debugger uno alla volta, ma i passaggi su funzioni anziché eseguire un'istruzione in tali (ancora viene eseguito il codice che si ignora).

Per altre informazioni sull'uso di modifica e continuazione e sulle limitazioni di funzionalità, vedere [modifica e continuazione](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger oltre a collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
