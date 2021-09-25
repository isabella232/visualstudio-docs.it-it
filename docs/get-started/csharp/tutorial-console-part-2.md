---
title: "Esercitazione 2: Estendere l'app console C#"
description: Informazioni su come sviluppare un'app console C# in Visual Studio, procedura dettagliata.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 86649110e83a9bce0768bddc81f148b3c4370793
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430532"
---
# <a name="tutorial-extend-c-console-app-and-debug-in-visual-studio-part-2-of-2"></a>Esercitazione: Estendere l'app console C# ed eseguire il debug in Visual Studio (parte 2 di 2)

Nella parte 2 di questa serie di esercitazioni si approfondirà ulteriormente Visual Studio funzionalità di compilazione e debug necessarie per lo sviluppo giornaliero. Queste funzionalità includono la gestione di più progetti, il debug e il riferimento a pacchetti di terze parti. Si esegue l'app console C# creata nella parte [1](tutorial-console.md)di questa esercitazione ed è possibile esplorare alcune funzionalità dell'ambiente di Visual Studio di sviluppo integrato (IDE). Questa esercitazione è la parte 2 di una serie di esercitazioni in due parti.

In questa esercitazione:

> [!div class="checklist"]
> * Aggiungere un secondo progetto.
> * Fare riferimento alle librerie e aggiungere pacchetti.
> * Eseguire altre operazioni di debug.
> * Esaminare il codice completato.


## <a name="prerequisites"></a>Prerequisiti

Per usare questo articolo, è possibile usare una di queste app calcolatrice:

- [L'app console Calculator della parte 1 di questa esercitazione.](tutorial-console.md)
- L'app Calcolatrice C# [nel repo vs-tutorial-samples](https://github.com/MicrosoftDocs/vs-tutorial-samples). Per iniziare, [aprire l'app dal repo.](../tutorial-open-project-from-repo.md)

## <a name="add-another-project"></a>Aggiungere un altro progetto

Il codice reale comporta la collaborazione di progetti in una soluzione. È possibile aggiungere un progetto di libreria di classi all'app Calcolatrice che fornisce alcune funzioni della calcolatrice.

In Visual Studio usare il comando di menu **File** Aggiungi nuovo Project  >    >   per aggiungere un nuovo progetto. È anche possibile fare clic con il pulsante destro del mouse sulla **soluzione** Esplora soluzioni per aggiungere un progetto dal menu di scelta rapida.

::: moniker range="vs-2019"
1. In **Esplora soluzioni** fare clic con il pulsante  destro del mouse sul nodo della soluzione e > **scegliere Aggiungi nuovo Project**.

1. Nella finestra **Aggiungi un nuovo progetto** digitare libreria di *classi* nella casella Di ricerca. Scegliere il modello di progetto **libreria di** classi C# e quindi selezionare **Avanti.**

   ![Screenshot della selezione del modello di progetto libreria di classi.](media/vs-2019/calculator2-add-project-dark.png)

1. Nella schermata **Configura il nuovo progetto** digitare il nome del progetto *CalculatorLibrary* e quindi selezionare **Avanti.**
   
1. Quando richiesto, scegliere .NET 3.1. Visual Studio crea il nuovo progetto e lo aggiunge alla soluzione.

   ![Screenshot della Esplora soluzioni con il progetto libreria di classi CalculatorLibrary aggiunto.](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Rinominare il file *Class1.cs* in *CalculatorLibrary.cs*. Per rinominare il file, è possibile fare clic con il pulsante destro del mouse sul nome in **Esplora soluzioni** e scegliere **Rinomina,** selezionare il nome e premere **F2** oppure selezionare il nome e fare di nuovo clic per digitare.

   Un messaggio potrebbe chiedere se si desidera rinominare i riferimenti `Class1` a nel file. Non è importante come rispondere, perché il codice verrà sostituito in un passaggio futuro.

1. Aggiungere ora un riferimento al progetto, in modo che il primo progetto possa usare le API esporrà la nuova libreria di classi. Fare clic con il pulsante **destro del mouse** sul nodo Dipendenze nel progetto **Calculator** e scegliere Aggiungi Project **riferimento**.

   ![Screenshot della voce di menu Aggiungi Project riferimento.](media/vs-2019/calculator2-add-project-reference-dark.png)

   Verrà visualizzata la finestra di dialogo **Gestione riferimenti**. In questa finestra di dialogo è possibile aggiungere riferimenti ad altri progetti, assembly e DLL COM necessari per i progetti.

1. Nella finestra **di dialogo Gestione** riferimenti selezionare la casella di controllo per il progetto **CalculatorLibrary** e quindi selezionare **OK.**

   ![Screenshot della finestra di dialogo Gestione riferimenti.](media/vs-2019/calculator2-ref-manager-dark.png)

   Il riferimento al progetto viene visualizzato in **un nodo Progetti** in **Esplora soluzioni**.

   ![Screenshot dell'Esplora soluzioni riferimento al progetto.](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. In *Program.cs* selezionare la `Calculator` classe e tutto il relativo codice e premere **CTRL** + **X** per tagliarla. In *CalculatorLibrary.cs* incollare quindi il codice nello spazio `CalculatorLibrary` dei nomi .
   
   Aggiungere anche `public` prima della classe Calculator per esporla all'esterno della libreria.

   *CalculatorLibrary.cs* dovrebbe ora essere simile al codice seguente:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. *Anche Program.cs* ha un riferimento, ma un errore indica che la `Calculator.DoOperation` chiamata non viene risolta. Questo perché si `CalculatorLibrary` trova in uno spazio dei nomi diverso. Per un riferimento completo, è possibile aggiungere lo spazio `CalculatorLibrary` dei nomi alla `Calculator.DoOperation` chiamata:

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   In caso contrario, è possibile provare ad aggiungere `using` una direttiva all'inizio del file:

   ```csharp
   using CalculatorLibrary;
   ```

   L'aggiunta della direttiva dovrebbe consentire di rimuovere lo spazio dei nomi dal sito di chiamata, ma ora si `using` `CalculatorLibrary` verifica un'ambiguità. La `Calculator` classe in o è lo spazio dei nomi `CalculatorLibrary` `Calculator` ?
   
   Per risolvere l'ambiguità, rinominare lo spazio dei nomi `Calculator` da `CalculatorProgram` a in *Program.cs* e *CalculatorLibrary.cs*.

   ```csharp
   namespace CalculatorProgram
   ```

::: moniker-end
::: moniker range=">=vs-2022"
1. In **Esplora soluzioni** fare clic con il pulsante  destro del mouse sul nodo della soluzione e > **scegliere Aggiungi nuovo Project**.

1. Nella finestra **Aggiungi un nuovo progetto** digitare libreria di *classi* nella casella Di ricerca. Scegliere il modello di progetto **libreria di** classi C# e quindi selezionare **Avanti.**

   ![Screenshot della selezione del modello di progetto libreria di classi.](media/vs-2022/calculator-add-project.png)

1. Nella schermata **Configura il nuovo progetto** digitare il nome del progetto *CalculatorLibrary* e quindi selezionare **Avanti.**
   
1. Nella schermata **Informazioni aggiuntive** è selezionato .NET 6.0. Selezionare **Crea**.
   
   Visual Studio crea il nuovo progetto e lo aggiunge alla soluzione.
   
   ![Screenshot della Esplora soluzioni con il progetto libreria di classi CalculatorLibrary aggiunto.](media/vs-2022/calculator-solution-explorer-with-class-library.png)

1. Rinominare il file *Class1.cs* in *CalculatorLibrary.cs*. Per rinominare il file, è possibile fare clic con il pulsante destro del mouse sul nome in **Esplora soluzioni** e scegliere **Rinomina,** selezionare il nome e premere **F2** oppure selezionare il nome e fare di nuovo clic per digitare.

   Un messaggio potrebbe chiedere se si desidera rinominare i riferimenti `Class1` a nel file. Non è importante come rispondere, perché il codice verrà sostituito in un passaggio futuro.

1. Aggiungere ora un riferimento al progetto, in modo che il primo progetto possa usare le API esporrà la nuova libreria di classi. Fare clic con il pulsante **destro del mouse** sul nodo Dipendenze nel progetto **Calculator** e scegliere Aggiungi Project **riferimento**.

   ![Screenshot della voce di menu Aggiungi Project riferimento.](media/vs-2022/calculator-add-project-reference.png)

   Verrà visualizzata la finestra di dialogo **Gestione riferimenti**. In questa finestra di dialogo è possibile aggiungere riferimenti ad altri progetti, assembly e DLL COM necessari per i progetti.

1. Nella finestra **di dialogo Gestione** riferimenti selezionare la casella di controllo per il progetto **CalculatorLibrary** e quindi selezionare **OK.**

   ![Screenshot della finestra di dialogo Gestione riferimenti.](media/vs-2022/calculator-reference-manager.png)

   Il riferimento al progetto viene visualizzato in **un nodo Progetti** in **Esplora soluzioni**.

   ![Screenshot dell'Esplora soluzioni riferimento al progetto.](media/vs-2022/calculator-solution-explorer-with-project-reference.png)

1. In *Program.cs* selezionare la `Calculator` classe e tutto il relativo codice e premere **CTRL** + **X** per tagliarla. In *CalculatorLibrary.cs* incollare quindi il codice nello spazio `CalculatorLibrary` dei nomi .
   
   Aggiungere anche `public` prima della classe Calculator per esporla all'esterno della libreria.

   *CalculatorLibrary.cs* dovrebbe ora essere simile al codice seguente:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. *Anche Program.cs* ha un riferimento, ma un errore indica che la `Calculator.DoOperation` chiamata non viene risolta. Questo perché si `CalculatorLibrary` trova in uno spazio dei nomi diverso. Per un riferimento completo, è possibile aggiungere lo spazio `CalculatorLibrary` dei nomi alla `Calculator.DoOperation` chiamata:

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   In caso contrario, è possibile provare ad aggiungere `using` una direttiva all'inizio del file:

   ```csharp
   using CalculatorLibrary;
   ```

   L'aggiunta della direttiva dovrebbe consentire di rimuovere lo spazio dei nomi dal sito di chiamata, ma ora si `using` `CalculatorLibrary` verifica un'ambiguità. La `Calculator` classe in o è lo spazio dei nomi `CalculatorLibrary` `Calculator` ?
   
   Per risolvere l'ambiguità, rinominare lo spazio dei nomi `Calculator` da `CalculatorProgram` a in *Program.cs* e *CalculatorLibrary.cs*.

   ```csharp
   namespace CalculatorProgram
   ```
::: moniker-end

## <a name="reference-net-libraries-write-to-a-log"></a>Fare riferimento alle librerie .NET: Scrivere in un log

È possibile usare la classe .NET per aggiungere un log di tutte `Trace` le operazioni e scriverlo in un file di testo. La `Trace` classe è utile anche per le tecniche di debug di stampa di base. La `Trace` classe è in e usa classi come `System.Diagnostics` `System.IO` `StreamWriter` .

1. Per iniziare, `using` aggiungere le direttive all'inizio di *CalculatorLibrary.cs:*

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Questo utilizzo della `Trace` classe deve contenere un riferimento per la classe , che associa a un filestream. Questo requisito significa che la calcolatrice funziona meglio come oggetto, quindi aggiungere un costruttore all'inizio della classe `Calculator` in *CalculatorLibrary.cs*.

   Rimuovere anche la `static` parola chiave per modificare il metodo statico in un metodo `DoOperation` membro.

   ```csharp
   public Calculator()
      {
          StreamWriter logFile = File.CreateText("calculator.log");
          Trace.Listeners.Add(new TextWriterTraceListener(logFile));
          Trace.AutoFlush = true;
          Trace.WriteLine("Starting Calculator Log");
          Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
      }

   public double DoOperation(double num1, double num2, string op)
      {
   ```

1. Aggiungere l'output del log a ogni calcolo. `DoOperation` dovrebbe ora essere simile al codice seguente:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. Tornando a *Program.cs,* una sottolineatura ondulata rossa contrassegna ora la chiamata statica. Per correggere l'errore, creare una `calculator` variabile aggiungendo la riga di codice seguente subito prima del ciclo `while (!endApp)` :

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Modificare anche il `DoOperation` sito di chiamata per fare riferimento all'oggetto denominato in lettere `calculator` minuscole. Il codice è ora una chiamata a un membro, anziché una chiamata a un metodo statico.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Eseguire nuovamente l'app. Al termine, fare clic con il pulsante destro del mouse sul nodo **del** progetto Calculator e scegliere **Apri cartella in Esplora file**.

1. In Esplora file passare alla cartella di output in *bin/Debug/* e aprire il file *calculator.log.* L'output dovrebbe essere simile al seguente:

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

A questo punto, *CalculatorLibrary.cs* dovrebbe essere simile al codice seguente:

```csharp
using System;
using System.IO;
using System.Diagnostics;


namespace CalculatorLibrary
{
    public class Calculator
    {

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.

            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                    break;
                case "s":
                    result = num1 - num2;
                    Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                    break;
                case "m":
                    result = num1 * num2;
                    Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            return result;
        }
    }
}
```

*Program.cs* dovrebbe essere simile al codice seguente:

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Aggiungere un pacchetto NuGet: Scrivere in un file JSON

Per eseguire operazioni di output in JSON, un formato comune e portabile per l'archiviazione dei dati degli oggetti, è possibile fare riferimento al pacchetto NuGet *Newtonsoft.Json.* NuGet pacchetti sono il metodo di distribuzione principale per le librerie di classi .NET.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Dipendenze** per il progetto **CalculatorLibrary** e **scegliere Gestisci** NuGet progetto .

   ::: moniker range="vs-2019"
   ![Screenshot di Gestisci NuGet pacchetti nel menu di scelta rapida.](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Screenshot di Gestisci NuGet pacchetti nel menu di scelta rapida.](media/vs-2022/calculator-manage-nuget-packages.png)
   ::: moniker-end

   Verrà NuGet Gestione pacchetti la finestra di dialogo.

   ::: moniker range="vs-2019"
   ![Screenshot del NuGet Gestione pacchetti.](media/vs-2019/calculator2-nuget-package-manager-dark.png)
   ::: moniker-end

1. Cercare e selezionare il *pacchetto Newtonsoft.Json* e selezionare **Installa.**

   ::: moniker range="vs-2019"
   ![Screenshot di Newtonsoft J SON NuGet informazioni sul pacchetto nel NuGet Gestione pacchetti.](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)
   
   Visual Studio scarica il pacchetto e lo aggiunge al progetto. Viene visualizzata una nuova voce nel nodo Riferimenti in **Esplora soluzioni**.
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Screenshot di Newtonsoft J SON NuGet informazioni sul pacchetto nel NuGet Gestione pacchetti.](media/vs-2022/calculator-nuget-newtonsoft-json.png)
   Se viene chiesto se accettare le modifiche, selezionare **OK.**
   
   Visual Studio scarica il pacchetto e lo aggiunge al progetto. Viene visualizzata una nuova voce in **un nodo Pacchetti** in **Esplora soluzioni**.
   ::: moniker-end

1. Aggiungere una `using` direttiva per `Newtonsoft.Json` all'inizio di *CalculatorLibrary.cs.*

   ```csharp
   using Newtonsoft.Json;
   ```

1. Creare `JsonWriter` l'oggetto membro e sostituire `Calculator` il costruttore con il codice seguente:

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. Modificare il `DoOperation` metodo per aggiungere il codice `writer` JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. Aggiungere un metodo per completare la sintassi JSON dopo che l'utente ha immesso i dati dell'operazione.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. Alla fine di *Program.cs,* prima di `return;` , aggiungere una chiamata a `Finish` :

   ```csharp
            // Add call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Compilare ed eseguire l'app e dopo aver immesso alcune operazioni, chiudere l'app immettendo il *comando n.*
   
1. Aprire il file *calculatorlog.json* in Esplora file. Verrà visualizzato un contenuto simile al seguente:

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>Debug: impostare e raggiunto un punto di interruzione

Il debugger Visual Studio è uno strumento potente. Il debugger può scorrere il codice per trovare il punto esatto in cui si verifica un errore di programmazione. È quindi possibile comprendere quali correzioni è necessario apportare e apportare modifiche temporanee per poter continuare a eseguire l'app.

1. In *Program.cs* fare clic nella barra di spostamento a sinistra della riga di codice seguente. È anche possibile fare clic sulla riga e premere **F9** oppure fare clic con il pulsante destro del mouse sulla riga e scegliere Punto di **interruzione** Inserisci punto  >  **di interruzione**.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Il punto rosso visualizzato indica un punto di interruzione. È possibile usare i punti di interruzione per sospendere l'app ed esaminare il codice. È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile.

   ![Screenshot che mostra l'impostazione di un punto di interruzione.](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Compilare ed eseguire l'app. Immettere i valori seguenti per il calcolo:

   - Per il primo numero immettere *8*.
   - Per il secondo numero immettere *0.*
   - Per l'operatore , diamo un po' di tempo. Immettere *d*.

   L'app sospende la posizione in cui è stato creato il punto di interruzione, indicato dal puntatore giallo a sinistra e dal codice evidenziato. Il codice evidenziato non è ancora stato eseguito.

   ![Screenshot del clic su un punto di interruzione](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Ora, con l'app sospesa, è possibile controllare lo stato dell'applicazione.

## <a name="debug-view-variables"></a>Debug: Visualizzare le variabili

1. Nel codice evidenziato passare il mouse su variabili come `cleanNum1` e `op` . I valori correnti per queste variabili `8` e, `d` rispettivamente, vengono visualizzati nei suggerimenti dati.

   ![Screenshot che mostra la visualizzazione di un suggerimento dati.](media/vs-2019/calculator-2-debug-view-datatip.png)

   Durante il debug, verificare se le variabili contengono i valori previsti è spesso fondamentale per risolvere i problemi.

2. Nel riquadro inferiore esaminare la **finestra Variabili** locali. Se è chiuso, selezionare **Debug**  >  **Windows**  >  **variabili locali** per aprirlo.

   La **finestra Variabili** locali mostra ogni variabile attualmente in ambito, insieme al valore e al tipo.

   ::: moniker range="vs-2019"
   ![Screenshot della finestra Variabili locali.](media/vs-2019/calculator-2-debug-locals-window.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Screenshot della finestra Variabili locali.](media/vs-2022/calculator-debug-locals-window.png)
   ::: moniker-end

3. Esaminare la **finestra Auto.**

   La finestra Auto è  simile alla finestra Variabili locali, ma mostra le variabili immediatamente prima e dopo la riga di codice corrente in cui l'app è sospesa.

Eseguire quindi il codice nel debugger un'istruzione alla volta, denominata *esecuzione istruzione per istruzione.*

## <a name="debug-step-through-code"></a>Debug: esecuzione istruzione per istruzione del codice

1. Premere **F11** o selezionare **Esegui debug**  >  **istruzione.**

   Usando il comando Esegui istruzione, l'app esegue l'istruzione corrente e passa all'istruzione eseguibile successiva, in genere la riga di codice successiva. Il puntatore giallo a sinistra indica sempre l'istruzione corrente.

   ![Screenshot del comando per l'esecuzione di istruzioni](media/vs-2019/calculator-2-debug-step-into.png)

   È stato appena fatto clic `DoOperation` sul metodo nella classe `Calculator` .

1. Per ottenere un'analisi gerarchica del flusso del programma, esaminare la finestra **Stack di** chiamate. Se è chiuso, selezionare **Debug** Windows  >    >  **stack di chiamate** per aprirlo.

   ![Screenshot dello stack di chiamate](media/vs-2019/calculator-2-debug-call-stack.png)

   Questa visualizzazione mostra il metodo `Calculator.DoOperation` corrente, indicato dal puntatore giallo. La seconda riga mostra la funzione che ha chiamato il metodo dal `Main` metodo in *Program.cs.*
   
   La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. Questa finestra consente anche di accedere a molte funzionalità del debugger, ad esempio Vai al codice **sorgente**, dal relativo menu di scelta rapida.

1. Premere **F10 o** selezionare Esegui **debug** istruzione/istruzione, più volte fino a quando  >  l'app non viene sospesa `switch` nell'istruzione.

   ```csharp
   switch (op)
   {
   ```

   Il comando Istruzione/istruzione è simile al comando Istruzione/istruzione, ad eccezione del fatto che se l'istruzione corrente chiama una funzione, il debugger esegue il codice nella funzione e non sospende l'esecuzione fino a quando la funzione non viene restituita. Se non si è interessati a una funzione specifica, l'esecuzione di un'istruzione/istruzione è più veloce rispetto all'esecuzione di un'istruzione/istruzione.

1. Premere **F10** ancora una volta, in modo che l'app si sospende nella riga di codice seguente.

   ```csharp
   if (num2 != 0)
   {
   ```

   Questo codice verifica la presenza di un caso di divisione per zero. Se l'app continua, verrà generata un'eccezione generale (errore), ma è possibile provare a eseguire un'altra operazione, ad esempio visualizzare il valore restituito effettivo nella console. Un'opzione è usare una funzionalità del debugger denominata *modifica e* continuazione per apportare modifiche al codice e quindi continuare il debug. Tuttavia, esiste un altro modo per modificare temporaneamente il flusso di esecuzione.

## <a name="debug-test-a-temporary-change"></a>Debug: testare una modifica temporanea

1. Selezionare il puntatore giallo, attualmente sospeso `if (num2 != 0)` sull'istruzione, e trascinarlo nell'istruzione seguente:

   ```csharp
   result = num1 / num2;
   ```

   Se si trascina il puntatore qui, l'app ignora completamente l'istruzione, in modo da poter vedere cosa accade `if` quando si divide per zero.

1. Premere **F10** per eseguire la riga di codice.

1. Se si passa il `result` puntatore del mouse sulla variabile, viene visualizzato il valore **Infinity**. In C# l'infinito è il risultato quando si divide per zero.

1. Premere **F5 o** selezionare **Debug**  >  **Continua debug**.

   Il simbolo infinito viene visualizzato nella console come risultato dell'operazione matematica.

1. Chiudere correttamente l'app immettendo *il comando n.*

## <a name="code-complete"></a>Completamento del codice

Ecco il codice completo per il file *CalculatorLibrary.cs,* dopo aver completato tutti i passaggi:

```csharp
using System;
using System.IO;
using System.Diagnostics;
using Newtonsoft.Json;

namespace CalculatorLibrary
{
    public class Calculator
    {

        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }

        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }

        public void Finish()
        {
            writer.WriteEndArray();
            writer.WriteEndObject();
            writer.Close();
        }
    }
}
```

Ed ecco il codice per *Program.cs:* 

```csharp
using System;
using CalculatorLibrary;

namespace CalculatorProgram
{
   
    class Program
    {
        static void Main(string[] args)
        {
            bool endApp = false;
            // Display title as the C# console calculator app.
            Console.WriteLine("Console Calculator in C#\r");
            Console.WriteLine("------------------------\n");

            Calculator calculator = new Calculator();
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
                    result = calculator.DoOperation(cleanNum1, cleanNum2, op); 
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
            calculator.Finish();
            return;
        }
    }
}
```

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, continuare con il contenuto seguente:

- [Continuare con altre esercitazioni su C#.](/dotnet/csharp/tutorials/)
- [Avvio rapido: Creare un'ASP.NET Core'app Web](../../ide/quickstart-aspnet-core.md).
- [Informazioni su come eseguire il debug del codice C# in Visual Studio](tutorial-debugger.md).
- [Viene illustrato come creare ed eseguire unit test.](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Eseguire un programma C#.](run-program.md)
- [Informazioni su IntelliSense per C#.](../../ide/visual-csharp-intellisense.md)
- [Continuare con la panoramica Visual Studio'IDE di .](visual-studio-ide.md)
