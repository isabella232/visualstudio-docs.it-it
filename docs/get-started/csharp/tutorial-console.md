---
title: "Esercitazione: Creare un'app console C# semplice"
description: Informazioni dettagliate su come creare un'app console C# in Visual Studio.
ms.custom: seodec18, get-started
ms.date: 01/25/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 79a29fa8b0d512049bf604668d11ea92e2511984
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2019
ms.locfileid: "56156072"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio"></a>Esercitazione: Creare un'app console C# semplice in Visual Studio

In questa esercitazione per C# si userà Visual Studio per creare ed eseguire un'app console ed esplorare nello stesso tempo alcune funzionalità dell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) di Visual Studio.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, si creerà un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

1. Aprire Visual Studio 2017.

2. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al file il nome *CalculateThis*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Aggiungere un gruppo di lavoro (facoltativo)

Se il modello di progetto **Console App (.NET Core)** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo multipiattaforma .NET Core**. Ecco come fare.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto

1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti

1. Chiudere la finestra di dialogo **Nuovo progetto** e sulla barra dei menu in alto scegliere **Strumenti** > **Ottieni strumenti e funzionalità**.

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

## <a name="create-the-app"></a>Creare l'app

Prima di tutto si esamineranno alcuni calcoli matematici integer di base in C#. Si aggiungerà quindi il codice necessario per creare una calcolatrice di base. Successivamente, si modificherà il codice per aggiungere funzionalità. In seguito, si procederà al debug dell'app per trovare eventuali errori e correggerli. E infine si perfezionerà il codice per renderlo più efficiente.

Si inizierà con alcuni calcoli matematici integer in C#.

1. Nell'editor del codice, eliminare il codice "Hello World" predefinito.

    ![Eliminare il codice Hello World predefinito dalla nuova app Calculator](./media/csharp-console-calculator-deletehelloworld.png)

   In particolare, eliminare la riga con la dicitura `Console.WriteLine("Hello World!");`.

1. Al suo posto digitare il codice seguente:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```
1. Scegliere **Calculator** per eseguire il programma oppure premere **F5**.

   ![Scegliere il pulsante Calculator per eseguire l'app dalla barra degli strumenti](./media/csharp-console-calculator-button.png)

   Si apre una finestra della console che visualizza la somma di 42 + 119.

1. Provare ora a modificare la riga di codice `int c = a + b;` con un operatore diverso, ad esempio `-` per la sottrazione, `*` per la moltiplicazione o */* per la divisione.

    Si noti che quando si cambia l'operatore e si esegue il programma, anche il risultato cambia.

Si continuerà aggiungendo un set più complesso di codice di calcolo al progetto.

1. Eliminare tutto il codice visualizzato nell'editor del codice.

1. Digitare o incollare il codice seguente nell'editor del codice:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```
1. Scegliere **Calculator** per eseguire il programma oppure premere **F5**.

   ![Scegliere il pulsante Calculator per eseguire l'app dalla barra degli strumenti](./media/csharp-console-calculator-button.png)

   Viene visualizzata una finestra della console.

1. Visualizzare l'app nella finestra della console, quindi seguire il prompt per aggiungere i numeri **42** e **119**.

   L'app avrà un aspetto simile allo screenshot seguente:

    ![Finestra della console che mostra l'app Calculator, che include i prompt sulle azioni da eseguire](./media/csharp-console-calculator.png)

### <a name="add-decimals"></a>Aggiungere i numeri decimali

L'app Calculator attualmente accetta e restituisce numeri interi. Tuttavia, sarà più precisa se si aggiunge il codice che consente di elaborare numeri decimali.

Come illustrato nello screenshot seguente, se si esegue l'app e si divide il numero 42 per 119, si ottiene come risultato 0, che non è esatto.

![Finestra della console con l'app Calculator che non restituisce valori numerici decimali nel risultato](./media/csharp-console-calculator-nodecimal.png)

È necessario correggere il codice in modo che gestisca i numeri decimali.

1. Premere **CTRL** + **F** per aprire il controllo **Trova e sostituisci**.

1. Sostituire ogni istanza della variabile `int` con `float`.

    ![Animazione del controllo Trova e sostituisci che illustra come modificare la variabile di tipo int in float](./media/find-replace-control-animation.gif)

1. Eseguire nuovamente l'app Calculator e dividere il numero **42** per il numero **119**.

   Si noti che l'app ora restituisce un valore numerico decimale invece di zero.

    ![Finestra della console con l'app Calculator che restituisce valori numerici decimali nel risultato](./media/csharp-console-calculator-decimal.png)

Tuttavia, l'app genera solo un risultato decimale. Modificando ancora il codice, è possibile fare in modo che l'app esegua anche calcoli con numeri decimali.

1. Usare il controllo **Trova e sostituisci** (**CTRL** + **F**) per sostituire ogni istanza della variabile `float` con `double` e quindi sostituire ogni istanza del metodo `Convert.ToInt32` con `Convert.ToDouble`.

1. Eseguire nuovamente l'app Calculator e dividere il numero **42,5** per il numero **119,75**.

   Si noti che l'app ora accetta valori decimali e restituisce un valore numerico decimale più lungo come risultato.

    ![Finestra della console con l'app Calculator che accetta valori decimali e restituisce un valore numerico decimale più lungo come risultato](./media/csharp-console-calculator-usedecimals.png)

    Il numero di posizioni decimali verrà modificato nella sezione [Rivedere il codice](#revise-the-code).

## <a name="debug-the-app"></a>Eseguire il debug dell'app

L'app Calculator di partenza è stata migliorata, ma non comprende ancora funzioni di sicurezza in grado di gestire le eccezioni, ad esempio gli errori di input dell'utente.

Ad esempio, se si tenta di dividere un numero per zero oppure di immettere un carattere alfabetico quando l'app si aspetta un carattere numerico (o viceversa), l'app smette di funzionare e restituisce un errore.

Si procederà ora a esaminare alcuni errori di input comuni degli utenti, individuandoli nel debugger e risolvendoli nel codice.

>[!TIP]
>Per altre informazioni sul debugger e sul suo funzionamento, vedere la pagina [Presentazione del debugger di Visual Studio](../../debugger/debugger-feature-tour.md).

### <a name="fix-the-divide-by-zero-error"></a>Correggere l'errore di divisione per zero

Quando si tenta di dividere un numero per zero, l'app console si blocca. Visual Studio mostra quindi qual è il problema nell'editor del codice.

   ![L'editor del codice di Visual Studio mostra l'errore di divisione per zero](./media/csharp-console-calculator-dividebyzero-error.png)

Ora il codice verrà modificato per gestire questo errore.

1. Eliminare il codice che viene visualizzato tra `case "d":` e il commento con la dicitura `// Wait for the user to respond before closing`.

1. Sostituirlo con il seguente codice:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Dopo aver aggiunto il codice, la sezione con l'istruzione `switch` avrà un aspetto simile a quello riportato nello screenshot seguente:

   ![Sezione "switch" aggiornata nell'editor del codice di Visual Studio](./media/csharp-console-calculator-switch-code.png)

Ora, quando si divide un numero qualsiasi per zero, l'app richiederà un altro numero. Anzi, continua a richiedere un numero diverso da zero finché l'utente non ne fornisce uno.

   ![L'editor del codice di Visual Studio mostra l'errore di divisione per zero](./media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Correggere l'errore di formato

Se si immette un carattere alfabetico quando l'app si aspetta un carattere numerico (o viceversa), l'app console si blocca. Visual Studio mostra quindi qual è il problema nell'editor del codice.

   ![L'editor del codice di Visual Studio mostra un errore di formato](./media/csharp-console-calculator-format-error.png)

Per correggere questo errore, è necessario effettuare il refactoring del codice immesso in precedenza.

#### <a name="revise-the-code"></a>Rivedere il codice

Anziché affidare la gestione dell'intero codice alla classe `program`, si dividerà l'app in due classi: `calculator` e `program`.

La classe `calculator` si occuperà di gestire la maggior parte del lavoro di calcolo mentre la classe `program` gestirà l'interfaccia utente e il lavoro di acquisizione degli errori.

Ma veniamo al dunque.

1. Eliminare tutto quanto compare *dopo* il blocco di codice seguente:

    ```csharp

    using System;

    namespace Calculator
    {

    ```

1. Successivamente, aggiungere una nuova classe `calculator`, come indicato di seguito:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Quindi, aggiungere una nuova classe `program`, come indicato di seguito:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
    ```
1. Scegliere **Calculator** per eseguire il programma oppure premere **F5**.

1. Seguire le istruzioni e dividere il numero **42** per il numero **119**. L'app avrà un aspetto simile a quello riportato nella figura seguente:

    ![Finestra della console con l'app Calculator sottoposta a refactoring che ora include prompt per le azioni da intraprendere e gestione degli errori per gli input non corretti](./media/csharp-console-calculator-refactored.png)

    Si noti che è disponibile l'opzione per immettere più equazioni fino a quando non si sceglie di chiudere l'app console. Inoltre, è anche stato ridotto il numero di posizioni decimali nel risultato.

## <a name="close-the-app"></a>Chiudere l'app

1. Se non si è già provveduto, chiudere l'app Calculator.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Chiudere il riquadro Output in Visual Studio](./media/csharp-calculator-close-output-pane.png)

1. In Visual Studio premere **CTRL**+**S** per salvare l'app.

1. Chiudere Visual Studio.

## <a name="code-complete"></a>Completamento del codice

Durante questa esercitazione sono state apportate molte modifiche all'app Calculator. L'app ora gestisce le risorse di calcolo in modo più efficiente e la maggior parte degli errori di input dell'utente.

Ecco il codice completo:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error

            // Use a switch statement to do the math
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    break;
                case "s":
                    result = num1 - num2;
                    break;
                case "m":
                    result = num1 * num2;
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry
                default:
                    break;
            }
            return result;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator
                Console.WriteLine("Choose an operator from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                string op = Console.ReadLine();

                try
                {
                    result = Calculator.DoOperation(cleanNum1, cleanNum2, op);
                    if (double.IsNaN(result))
                    {
                        Console.WriteLine("This operation will result in a mathematical error.\n");
                    }
                    else Console.WriteLine("Your result: {0:0.##}\n", result);
                }
                catch (Exception e)
                {
                    Console.WriteLine("Oh no! An exception occurred trying to do the math.\n - Details: " + e.Message);
                }

                Console.WriteLine("------------------------\n");

                // Wait for the user to respond before closing
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Altre esercitazioni su C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Vedere anche

* [Informazioni sul debug del codice C# in Visual Studio](tutorial-debugger.md)