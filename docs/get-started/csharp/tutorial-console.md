---
title: 'Esercitazione: Creare una semplice app console C# '
description: Informazioni dettagliate su come creare un'app console C# in Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e46b3ed2449972b065ac005ac83f2650cb93d03d
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128426684"
---
# <a name="tutorial-create-a-simple-c-console-app-in-visual-studio-part-1-of-2"></a>Esercitazione: Creare una semplice app console C# in Visual Studio (parte 1 di 2)

In questa esercitazione si userà Visual Studio per creare ed eseguire un'app console C# ed esplorare alcune funzionalità dell'ambiente Visual Studio di sviluppo integrato (IDE). Questa esercitazione è la parte 1 di una serie di esercitazioni in due parti.

In questa esercitazione:

> [!div class="checklist"]
> * Creare un Visual Studio progetto.
> * Creare un'app console C#.
> * Eseguire il debug dell'app.
> * Chiudere l'app.
> * Esaminare il codice completo.

[Nella parte 2](tutorial-console-part-2.md)si estende questa app per aggiungere altri progetti, apprendere i consigli di debug e fare riferimento a pacchetti di terze parti.

## <a name="prerequisites"></a>Prerequisiti

È necessario aver installato Visual Studio.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per iniziare, creare un progetto di applicazione C#. Il tipo di progetto include tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**.
   In alternativa, premere **CTRL** + **MAIUSC** + **N**).

3. Nel riquadro a sinistra della finestra di dialogo **Nuovo progetto** espandere **C#** e scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al file il **_nome Calculator_**.

   ![Screenshot che mostra il modello di progetto App console (.NET Core) nella finestra di dialogo Nuovo Project nell'IDE Visual Studio.](./media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workload-optional"></a>Aggiungere un carico di lavoro (facoltativo)

Se il modello di progetto **Console App (.NET Core)** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo multipiattaforma .NET Core**. Ecco come.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto

1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Screenshot che mostra il collegamento Choose the Open Programma di installazione di Visual Studio (Programma di installazione di Visual Studio apri) nella finestra di dialogo Project nuova finestra di dialogo.](./media/csharp-open-visual-studio-installer-generic-dark.png)

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Screenshot che mostra il carico di lavoro Sviluppo multipiattaforma .NET Core nella Programma di installazione di Visual Studio.](./media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti

1. Annullare dalla finestra **di dialogo Project** e dalla barra dei  menu superiore scegliere Strumenti Ottieni strumenti > **e funzionalità.**

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio e scegliere **Crea un nuovo progetto** nella finestra Iniziale.

   ![Screenshot che mostra la finestra Crea un nuovo progetto.](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** scegliere **C#** dall'elenco Linguaggio. Scegliere quindi **Windows** dall'elenco Piattaforma e **Console** dall'elenco dei tipi di progetto.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il **modello Applicazione** console e quindi selezionare **Avanti.**

   > [!NOTE]
   > Se il modello Applicazione **console** non è visualizzato, selezionare **Installa altri strumenti e funzionalità.**
   >
   > ![Screenshot che mostra il collegamento Installa altri strumenti e funzionalità.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.
   >
   > ![Screenshot che mostra il carico di lavoro Sviluppo multipiattaforma .NET Core nella Programma di installazione di Visual Studio.](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro. Quindi tornare al passaggio 2 della procedura [Creare un progetto](#create-a-project)".

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *Calculator* nella casella **Nome del progetto**. Scegliere quindi **Avanti.**

    :::image type="content" source="./media/vs-2019/csharp-name-your-calculator-project.png" alt-text="Screenshot che mostra il nome del progetto &quot;Calculator&quot; nella finestra &quot;Configure your new project&quot; (Configura il nuovo progetto).":::

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già **selezionato .NET Core 3.1** per il framework di destinazione. In caso contrario, **selezionare .NET Core 3.1.** Scegliere quindi **Crea.**

    :::image type="content" source="./media/vs-2019/csharp-target-framework.png" alt-text="Screenshot che mostra come assicurarsi che .NET Core 3.1 sia selezionato nella finestra &quot;Informazioni aggiuntive&quot;.":::

   Visual Studio aprirà il nuovo progetto che include il codice "Hello World" predefinito.

::: moniker-end
::: moniker range=">=vs-2022"

1. Aprire Visual Studio e scegliere **Crea un nuovo progetto** nella finestra Iniziale.

   ![Screenshot che mostra la finestra Crea un nuovo progetto.](media/vs-2022/create-new-project.png)

1. Nella finestra **Crea un nuovo progetto** selezionare Tutti i **linguaggi** e quindi scegliere **C#** dall'elenco a discesa. Scegliere **Windows** dall'elenco **Tutte le** piattaforme e scegliere **Console** dall'elenco Tutti i **tipi di** progetto.

   Dopo aver applicato i filtri del linguaggio, della piattaforma e del tipo di progetto, scegliere il **modello Applicazione** console e quindi selezionare **Avanti.**

   > [!NOTE]
   > Se il modello Applicazione **console** non è visualizzato, selezionare **Installa altri strumenti e funzionalità.**
   >
   > ![Screenshot che mostra il collegamento Installa altri strumenti e funzionalità.](media/vs-2022/not-finding-what-looking-for.png)
   >
   > Nell'Programma di installazione di Visual Studio scegliere il carico **di lavoro Sviluppo per desktop .NET** e quindi selezionare **Modifica.**
   >
   > ![Screenshot che mostra il carico di lavoro Sviluppo di applicazioni desktop .NET nel Programma di installazione di Visual Studio.](media/vs-2022/dot-net-development-workload.png)

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *Calculator* nella casella Project **nome** e quindi selezionare **Avanti.**

   ![Screenshot che mostra come assegnare un nome al progetto Calculator nella finestra Configura il nuovo progetto.](media/vs-2022/csharp-name-your-calculator-project.png)

1. Nella finestra **Informazioni aggiuntive** dovrebbe essere già selezionato **.NET 6.0** per il framework di destinazione. Selezionare **Crea**.

   ![Screenshot che mostra .NET 6.0 selezionato nella finestra Informazioni aggiuntive.](media/vs-2022/csharp-target-framework.png)

   Visual Studio aprirà il nuovo progetto che include il codice "Hello World" predefinito.

::: moniker-end

## <a name="create-the-app"></a>Creare l'app

In questa sezione verrà illustrato come:

- Esplorare alcune operazioni matematiche di base su interi in C#.
- Aggiungere il codice per creare un'app calcolatrice di base.
- Eseguire il debug dell'app per trovare e correggere gli errori.
- Perfezionare il codice per renderlo più efficiente.

### <a name="explore-integer-math"></a>Esplorare le operazioni matematiche su interi

Iniziare con alcune operazioni matematiche di base su numeri interi in C#.

::: moniker range="<=vs-2019"
1. Nell'editor del codice, eliminare il codice "Hello World" predefinito.

    ![Screenshot che mostra l'eliminazione del codice Hello World predefinito dalla nuova app calcolatrice.](./media/csharp-console-calculator-deletehelloworld.png)

   In particolare, eliminare la riga con la dicitura `Console.WriteLine("Hello World!");`.

1. Al suo posto digitare il codice seguente:

    ```csharp
            int a = 42;
            int b = 119;
            int c = a + b;
            Console.WriteLine(c);
            Console.ReadKey();
    ```

    Sarà quindi possibile notare che la funzionalità IntelliSense in Visual Studio offrirà l'opzione per completare automaticamente l'inserimento.

    > [!NOTE]
    > L'animazione seguente non è progettata per duplicare il codice precedente. Lo scopo è mostrare solo il funzionamento della funzionalità di completamento automatico.

    ![Animazione del codice matematico integer che mostra la funzionalità di completamento automatico IntelliSense nell'IDE Visual Studio.](./media/integer-math-intellisense.gif)

1. Scegliere il pulsante **Start** verde accanto a **Calcolatrice** per compilare ed eseguire il programma oppure premere **F5.**

   ![Screenshot che mostra la scelta del pulsante Calcolatrice per eseguire l'app dalla barra degli strumenti.](./media/csharp-console-calculator-button.png)

   Si aprirà una finestra della console che visualizza la somma di 42 + 119., vale a dire **161**.

    ![Screenshot che mostra una finestra della console con i risultati delle operazioni matematiche su numeri interi.](./media/csharp-console-integer-math.png)

1. **(Facoltativo)** È possibile modificare l'operatore per modificare il risultato. Nella riga di codice `int c = a + b;` è ad esempio possibile modificare l'operatore `+` in `-` per la sottrazione, `*` per la moltiplicazione o `/` per la divisione. A questo punto, quando il programma sarà eseguito, il risultato cambierà.

1. Chiudere la finestra della console.
::: moniker-end

::: moniker range=">=vs-2022"
1. In **Esplora soluzioni** selezionare **Program.cs** nel riquadro destro per visualizzare il file nell'editor di codice

1. Nell'editor di codice sostituire il codice predefinito "Hello World" che indica `Console.WriteLine("Hello World!");` .

    ![Screenshot che mostra la riga da sostituire nel file di programma.](media/vs-2022/csharp-console-calculator-delete-hello-world.png)

   Sostituire la riga con il codice seguente:

   ```csharp
       int a = 42;
       int b = 119;
       int c = a + b;
       Console.WriteLine(c);
       Console.ReadKey();
   ```

    Se si digita il codice, la Visual Studio IntelliSense offre la possibilità di completare automaticamente la voce.

    > [!NOTE]
    > L'animazione seguente non ha lo scopo di illustrare il codice precedente, ma solo di mostrare il funzionamento di IntelliSense.

    ![Animazione del codice matematico integer che mostra la funzionalità di completamento automatico intelliSense nell'IDE Visual Studio.](media/integer-math-intellisense.gif)

1. Per compilare ed eseguire l'app, premere **F5** o selezionare la freccia verde accanto al nome **Calculator** nella barra degli strumenti superiore.

   ![Screenshot che mostra la selezione del pulsante Calcolatrice per eseguire l'app dalla barra degli strumenti Debug.](media/vs-2022/csharp-console-calculator-button.png)

   Verrà visualizzata una finestra della console che mostra la somma di 42 + 119, ovvero **161**.

    ![Screenshot di una finestra della console che mostra i risultati di numeri interi matematici.](media/vs-2022/csharp-console-integer-math.png)

1. Chiudere la finestra della console.

1. Facoltativamente, è possibile modificare l'operatore per modificare il risultato. Nella riga di codice `int c = a + b;` è ad esempio possibile modificare l'operatore `+` in `-` per la sottrazione, `*` per la moltiplicazione o `/` per la divisione. Quando si esegue l'app, il risultato cambia di conseguenza.

::: moniker-end

### <a name="add-code-to-create-a-calculator"></a>Aggiungere codice per creare un'app di calcolo

Continuare aggiungendo un set più complesso di codice calcolatrice al progetto.

1. Nell'editor di codice sostituire tutto il codice in *program.cs* con il nuovo codice seguente:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then initialize to zero.
                int num1 = 0; int num2 = 0;

                // Display title as the C# console calculator app.
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number.
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to type the second number.
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToInt32(Console.ReadLine());

                // Ask the user to choose an option.
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math.
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
                // Wait for the user to respond before closing.
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

1. Selezionare il **pulsante Calcolatrice** o premere **F5** per eseguire l'app.

   Viene visualizzata una finestra della console.

1. Nella finestra della console seguire le istruzioni per aggiungere insieme i numeri **42** **e 119.**

   L'app avrà un aspetto simile allo screenshot seguente:

    ![Screenshot di una finestra della console che mostra l'app Calcolatrice con prompt.](media/csharp-console-calculator.png)

### <a name="add-decimal-functionality"></a>Aggiungere la funzionalità decimale

Modificare ora il codice per aggiungere altre funzionalità.

L'app calcolatrice corrente accetta e restituisce solo numeri interi. Ad esempio, se si esegue l'app e si divide il numero 42 per il numero 119, il risultato è zero, che non è esatto.

![Screenshot di una finestra della console che mostra l'app Calcolatrice che restituisce un numero intero inesatto di conseguenza.](./media/csharp-console-calculator-nodecimal.png)

Per correggere il codice per migliorare la precisione gestendo i decimali:

1. Da *program.cs nell'editor* Visual Studio premere **CTRL** + **H** per aprire il **controllo** Trova e sostituisci.

1. Digitare *int* nel controllo e tipo *float* nel **campo Replace.**

1. Selezionare le icone **Maiuscole/minuscole** e Trova corrispondenza **per** parola intera nel controllo oppure premere **ALT** + **C** **e** + **ALT+W.**

1. Selezionare **l'icona Sostituisci** tutto o premere **ALT** + **A** per eseguire la ricerca e la sostituzione.

    ![Animazione del controllo Trova e sostituisci che mostra come modificare la variabile int in float.](media/find-replace-control-animation.gif)

1. Eseguire di nuovo l'app calcolatrice e dividere il **numero 42** per il **numero 119.**

   L'app ora restituisce un numero decimale anziché zero.

    ![Screenshot di una finestra della console che mostra l'app Calcolatrice che ora restituisce un numero decimale come risultato.](media/csharp-console-calculator-decimal.png)

Ora l'app può produrre risultati decimali. Apportare altre modifiche al codice in modo che l'app possa calcolare anche i decimali.

1. Usare il **controllo Trova e** sostituisci per modificare ogni istanza della variabile in e per impostare ogni istanza del metodo su `float` `double` `Convert.ToInt32` `Convert.ToDouble` .

1. Eseguire l'app calcolatrice e dividere il **numero 42,5** per il **numero 119,75.**

   L'app accetta ora valori decimali e restituisce un numero decimale più lungo come risultato.

    ![Screenshot di una finestra della console che mostra l'app Calcolatrice che ora accetta numeri decimali e restituisce un risultato decimale più lungo.](media/csharp-console-calculator-usedecimals.png)

   Nella sezione [Rivedi il codice](#revise-the-code) si riduce il numero di cifre decimali nei risultati.

## <a name="debug-the-app"></a>Eseguire il debug dell'app

L'app calcolatrice di base è stata migliorata, ma l'app non gestisce ancora le eccezioni, ad esempio gli errori di input dell'utente. Ad esempio, se gli utenti provano a dividere per zero o immettere un carattere imprevisto, l'app potrebbe smettere di funzionare, restituire un errore o restituire un risultato non numerico imprevisto.

Verranno ora visualizzati alcuni errori di input utente comuni, individuarli nel debugger, se presenti, e correggerli nel codice.

> [!TIP]
> Per altre informazioni sul debugger e sul suo funzionamento, vedere Prima di tutto esaminare il [debugger Visual Studio debugger](../../debugger/debugger-feature-tour.md).

### <a name="fix-the-divide-by-zero-error"></a>Correggere l'errore di divisione per zero

Se si tenta di dividere un numero per zero, è possibile che l'app console si blocchi e quindi venga visualizzato il problema nell'editor di codice.

   ![Screenshot dell'editor Visual Studio codice che mostra una riga evidenziata in giallo e un errore eccezione non gestita per 'Tentativo di divisione per zero'.](./media/csharp-console-calculator-dividebyzero-error.png)

> [!NOTE]
> In alcuni casi l'app non si blocca e il debugger non visualizza un errore di divisione per zero. L'app potrebbe invece restituire un risultato non numerico imprevisto, ad esempio un simbolo di infinito. La correzione di codice seguente si applica ancora.

Per modificare il codice per gestire l'errore:

1. In *program.cs* sostituire il codice tra `case "d":` e il commento che indica con il codice `// Wait for the user to respond before closing` seguente:

   ```csharp
            // Ask the user to enter a non-zero divisor until they do so.
                while (num2 == 0)
                {
                    Console.WriteLine("Enter a non-zero divisor: ");
                    num2 = Convert.ToInt32(Console.ReadLine());
                }
                Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                break;
        }
    ```

   Dopo aver sostituito il codice, la sezione con `switch` l'istruzione dovrebbe essere simile allo screenshot seguente:

   ![Screenshot che mostra la sezione dell'opzione modificata nell'editor Visual Studio codice.](media/csharp-console-calculator-switch-code.png)

Ora, quando si divide un numero per zero, l'app richiede un altro numero e continua a chiedere fino a quando non si specifica un numero diverso da zero.

   ![Screenshot di una finestra della console con un prompt ripetuto per specificare un numero diverso da zero.](media/csharp-console-calculator-dividebyzero.png)

### <a name="fix-the-format-error"></a>Correggere l'errore di formato

Se si immette un carattere alfabetico quando l'app prevede un carattere numerico, l'app si blocca. Visual Studio che cosa non va nell'editor di codice.

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra un errore di formato non gestito nell'editor Visual Studio codice.](media/csharp-console-calculator-format-error.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Screenshot che mostra un errore di formato non gestito nell'editor Visual Studio codice.](media/vs-2022/csharp-console-calculator-format-error.png)
   ::: moniker-end

Per evitare questa eccezione, è possibile eseguire il refactoring del codice immesso in precedenza.

#### <a name="revise-the-code"></a>Rivedere il codice

Anziché affidarsi alla `program` classe per gestire tutto il codice, è possibile dividere l'app in due classi: e `Calculator` `Program` .

La classe gestisce la maggior parte del lavoro di calcolo e la classe gestisce l'interfaccia utente e il `Calculator` lavoro di gestione degli `Program` errori.

A questo punto, procedere con l'esercitazione.

1. In *program.cs* eliminare tutti gli elementi nello spazio dei nomi tra le parentesi graffe di apertura `Calculator` e chiusura:

    ```csharp
    using System;

    namespace Calculator
    {

    }
    ```

1. Tra le parentesi graffe aggiungere la nuova `Calculator` classe seguente:

    ```csharp
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
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
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }

    ```

1. Aggiungere anche una nuova  `Program` classe, come indicato di seguito:

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
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

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
    ```

1. Selezionare il **pulsante Calcolatrice** o premere **F5** per eseguire l'app.

1. Seguire le istruzioni e dividere il numero **42** per il numero **119**. I risultati dovrebbero essere simili allo screenshot seguente:

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra una finestra della console con l'app Calculator con refactoring.](media/csharp-console-calculator-refactored.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Screenshot che mostra una finestra della console con l'app Calculator con refactoring.](media/vs-2022/csharp-console-calculator-refactored.png)
   ::: moniker-end

   È ora possibile immettere altre equazioni fino a quando non si sceglie di chiudere l'app console. Nei risultati sono presenti anche meno cifre decimali. Se si immette un carattere non corretto, si ottiene una risposta di errore appropriata.

## <a name="close-the-app"></a>Chiudere l'app

1. Se non è già stato fatto, chiudere l'app Calcolatrice.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Screenshot che mostra la chiusura del riquadro Output in Visual Studio.](media/csharp-calculator-close-output-pane.png)

1. In Visual Studio premere **CTRL** + **S** per salvare l'app.

[!INCLUDE[../includes/git-source-control.md](../includes/git-source-control.md)]

## <a name="review-code-complete"></a>Revisione: Codice completato

In questa esercitazione sono state apportate molte modifiche all'app calcolatrice. L'app ora gestisce le risorse di calcolo in modo più efficiente e gestisce la maggior parte degli errori di input dell'utente.

Ecco il codice completo:

```csharp

using System;

namespace Calculator
{
    class Calculator
    {
        public static double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
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
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                    }
                    break;
                // Return text for an incorrect option entry.
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
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            while (!endApp)
            {
                // Declare variables and set to empty.
                string numInput1 = "";
                string numInput2 = "";
                double result = 0;

                // Ask the user to type the first number.
                Console.Write("Type a number, and then press Enter: ");
                numInput1 = Console.ReadLine();

                double cleanNum1 = 0;
                while (!double.TryParse(numInput1, out cleanNum1))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput1 = Console.ReadLine();
                }

                // Ask the user to type the second number.
                Console.Write("Type another number, and then press Enter: ");
                numInput2 = Console.ReadLine();

                double cleanNum2 = 0;
                while (!double.TryParse(numInput2, out cleanNum2))
                {
                    Console.Write("This is not valid input. Please enter an integer value: ");
                    numInput2 = Console.ReadLine();
                }

                // Ask the user to choose an operator.
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

                // Wait for the user to respond before closing.
                Console.Write("Press 'n' and Enter to close the app, or press any other key and Enter to continue: ");
                if (Console.ReadLine() == "n") endApp = true;

                Console.WriteLine("\n"); // Friendly linespacing.
            }
            return;
        }
    }
}

```

## <a name="next-steps"></a>Passaggi successivi

:::moniker range="vs-2017"

Continuare con altre esercitazioni:

> [!div class="nextstepaction"]
> [Esercitazioni su C#](/dotnet/csharp/tutorials)

> [!div class="nextstepaction"]
> [Presentazione dell'IDE di Visual Studio](../visual-studio-ide.md)

:::moniker-end

:::moniker range=">=vs-2019"

Continuare con la seconda parte di questa esercitazione:

> [!div class="nextstepaction"]
> [Esercitazione Parte 2: Estendere ed eseguire il debug dell'app console C#](tutorial-console-part-2.md)
:::moniker-end
