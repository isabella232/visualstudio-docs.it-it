---
title: "Esercitazione 2: Estendere l'app console C#"
description: Informazioni su come sviluppare un'app console C# in Visual Studio, procedura dettagliata.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
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
ms.openlocfilehash: 2c8e0108a58e6502de9f8a52b7738ea055f6862f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049090"
---
# <a name="tutorial-extend-c-console-app-and-debug-in-visual-studio-part-2-of-2"></a>Esercitazione: Estendere l'app console C# ed eseguire il debug in Visual Studio (parte 2 di 2)

Nella parte 2 di questa serie di esercitazioni verranno approfondite le funzionalità di compilazione e debug di Visual Studio necessarie per lo sviluppo giornaliero, ad esempio la gestione di più progetti, il debug e il riferimento a pacchetti di terze parti. Si eseguirà l'app console C# creata in [Parte 1 di questa esercitazione(tutorial-console.md) ed esplorerà alcune funzionalità dell'ambiente di sviluppo integrato (IDE) di Visual Studio durante questa operazione. Questa esercitazione è la parte 2 di una serie di esercitazioni in due parti.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Aggiungere un altro progetto al primo.
> * Fare riferimento alle librerie e aggiungere pacchetti.
> * Eseguire il debug di altre informazioni.
> * Esaminare il codice completo.


## <a name="prerequisites"></a>Prerequisiti

È necessario:
+ Usare [l'app console Calculator della parte 1 di questa serie di esercitazioni](tutorial-console.md) 
+ Usare l'app Calcolatrice C# [nel repo vs-tutorial-samples](https://github.com/MicrosoftDocs/vs-tutorial-samples) che è possibile aprire da un [repo](../tutorial-open-project-from-repo.md) per iniziare.

## <a name="add-another-project"></a>Aggiungere un altro progetto

Il codice reale implica molti progetti che lavorano insieme in una soluzione. Ora si aggiunge un altro progetto all'app Calculator. Si tratta di una libreria di classi che fornisce alcune delle funzioni della calcolatrice.

1. In Visual Studio è possibile usare il comando di menu di primo livello **File** Aggiungi nuovo Project per aggiungere un nuovo progetto, ma è anche possibile fare clic con il pulsante destro del mouse sul nome del progetto esistente  >    >   (denominato "nodo del progetto") e aprire il menu di scelta rapida del progetto (o menu di scelta rapida). Questo menu di scelta rapida contiene molti modi per aggiungere funzionalità ai progetti. Fare quindi clic con il pulsante destro del mouse sul nodo **del progetto Esplora soluzioni** e scegliere Aggiungi  >  **nuovo Project**.

1. Scegliere il modello di progetto C# Libreria di **classi (.NET Standard)**.

   ![Screenshot della selezione del modello di progetto libreria di classi](media/vs-2019/calculator2-add-project-dark.png)

1. Digitare il nome del progetto **CalculatorLibrary** e scegliere **Crea**. Quando richiesto, scegliere di nuovo .NET 3.1. Visual Studio crea il nuovo progetto e lo aggiunge alla soluzione.

   ![Screenshot dell'Esplora soluzioni con il progetto libreria di classi CalculatorLibrary aggiunto](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Invece di avere *Class1.cs,* rinominare il file **CalculatorLibrary.cs**. È possibile fare clic sul nome **in** Esplora soluzioni rinominarlo oppure fare clic con il pulsante destro del mouse e scegliere **Rinomina** oppure premere **F2.**

   È possibile che venga chiesto se si vuole rinominare i riferimenti `Class1` a nel file. Non è importante come rispondere, poiché il codice verrà sostituito in un passaggio futuro.

1. È ora necessario aggiungere un riferimento al progetto, in modo che il primo progetto possa usare le API esposte dalla nuova libreria di classi.  Fare clic con il pulsante destro **del mouse** sul nodo Dipendenze nel primo progetto e scegliere Aggiungi Project **riferimento**.

   ![Screenshot della voce di menu Aggiungi Project riferimento](media/vs-2019/calculator2-add-project-reference-dark.png)

   Verrà visualizzata la finestra di dialogo **Gestione riferimenti**. Questa finestra di dialogo consente di aggiungere riferimenti ad altri progetti, nonché assembly e DLL COM necessari per i progetti.

   ![Screenshot della finestra di dialogo Gestione riferimenti](media/vs-2019/calculator2-ref-manager-dark.png)

1. Nella finestra **di dialogo Gestione** riferimenti selezionare la casella di controllo per il progetto **CalculatorLibrary** e scegliere **OK.**  Il riferimento al progetto viene visualizzato in **un nodo Progetti** in **Esplora soluzioni**.

   ![Screenshot dell'Esplora soluzioni riferimento al progetto](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. In *Program.cs* selezionare la classe e tutto il relativo codice `Calculator` e premere **CTRL+X** per tagliarla da Program.cs. In **CalculatorLibrary** in *CalculatorLibrary.cs* incollare quindi il codice nello spazio dei `CalculatorLibrary` nomi . Creare quindi la classe Calculator `public` per esporla all'esterno della libreria. Il codice in *CalculatorLibrary.cs* dovrebbe ora essere simile al codice seguente:

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
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
    }
   ```

1. Il primo progetto ha un riferimento, ma verrà visualizzato un errore che la chiamata Calculator.DoOperation non risolve. Questo perché CalculatorLibrary si trova in uno spazio dei nomi diverso, quindi aggiungere lo spazio dei `CalculatorLibrary` nomi per un riferimento completo.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Provare ad aggiungere una direttiva using all'inizio del file:

   ```csharp
   using CalculatorLibrary;
   ```

   Questa modifica dovrebbe consentire di rimuovere lo spazio dei nomi CalculatorLibrary dal sito di chiamata, ma ora si verifica un'ambiguità. La classe in CalculatorLibrary o `Calculator` Calculator è lo spazio dei nomi ?  Per risolvere l'ambiguità, rinominare lo spazio dei nomi `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Fare riferimento alle librerie .NET: scrivere in un log

1. Si supponga ora di voler aggiungere un log di tutte le operazioni e di scriverlo in un file di testo. La classe .NET `Trace` fornisce questa funzionalità. È utile anche per tecniche di debug di stampa di base.  La classe Trace si trova in System.Diagnostics ed è necessario System.IO classi come , quindi iniziare aggiungendo le direttive using all'inizio `StreamWriter` di *CalculatorLibrary.cs:*

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Osservando come viene usata la classe Trace, è necessario mantenere un riferimento per la classe , associato a un filestream. Ciò significa che la calcolatrice funziona meglio come oggetto, quindi si aggiunge un costruttore all'inizio della classe Calculator in *CalculatorLibrary.cs.*

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

1. Ed è necessario modificare il metodo statico `DoOperation` in un metodo membro, quindi rimuovere la parola `static` chiave .  Si aggiunge anche l'output a ogni calcolo per il log, in modo che DoOperation sia simile al codice seguente:

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

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

1. Ora di nuovo in *Program.cs,* la chiamata statica viene contrassegnata con un rosso ondulato. Per risolvere il problema, creare `calculator` una variabile aggiungendo la riga seguente subito prima del `while (!endApp)` ciclo:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Modificare il sito di chiamata per come indicato di seguito, in modo che faccia riferimento all'oggetto denominato in lettere minuscole, rendendo così questa chiamata a un membro anziché a una chiamata `DoOperation` `calculator` a un metodo statico:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Eseguire di nuovo il programma e, al termine, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere Apri cartella **in Esplora file**, quindi spostarsi verso il basso Esplora file alla cartella di output. Potrebbe essere *bin/Debug/netcoreapp3.1* e aprire il file *calculator.log.*

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

A questo punto, *CalculatorLibrary.cs* dovrebbe avere un aspetto simile al seguente:

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
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

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

*Program.cs dovrebbe* essere simile al seguente:

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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Aggiungere un NuGet pacchetto: scrivere in un file JSON

1. Si supponga ora di voler eseguire l'output delle operazioni in un formato JSON, un formato comune e portabile per l'archiviazione dei dati degli oggetti. Per implementare questa funzionalità, è necessario fare riferimento al NuGet pacchetto Newtonsoft.Jssu . NuGet pacchetti sono il veicolo principale per la distribuzione delle librerie di classi .NET. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Dipendenze** per il progetto CalculatorLibrary e scegliere Gestisci NuGet **pacchetti**.

   ![Screenshot di Gestisci NuGet pacchetti nel menu di scelta rapida](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Verrà NuGet Gestione pacchetti la finestra di dialogo.

   ![Screenshot di Gestione pacchetti NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Cercare Newtonsoft.Jsnel pacchetto e scegliere **Installa**.

   ![Screenshot delle informazioni sul pacchetto NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Il pacchetto viene scaricato e aggiunto al progetto e viene visualizzata una nuova voce nel nodo Riferimenti in **Esplora soluzioni**.

1. Aggiungere una direttiva using per System.IO e Newtonsoft.Jspacchetto all'inizio di *CalculatorLibrary.cs.*

   ```csharp
   using Newtonsoft.Json;
   ```

1. Sostituire ora il costruttore per Calculator con il codice seguente e creare l'oggetto membro JsonWriter:

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

1. Modificare il `DoOperation` metodo per aggiungere il codice del writer JSON:

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
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

1. È necessario aggiungere un metodo per completare la sintassi JSON dopo che l'utente ha completato l'immissione dei dati dell'operazione.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. In *Program.cs* aggiungere una chiamata a Finish alla fine.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Compilare ed eseguire l'app e, dopo aver immesso alcune operazioni, chiudere correttamente l'app usando il comando 'n'.  A questo punto, aprire calculatorlog.jsfile e verrà visualizzato un messaggio simile al seguente:

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

## <a name="debug-set-and-hit-a-breakpoint"></a>Debug: impostare e premere un punto di interruzione

Il debugger Visual Studio è uno strumento potente che consente di eseguire il codice passo dopo passo, per trovare il punto esatto in cui si è commesso un errore di programmazione. È quindi possibile comprendere quali correzioni è necessario apportare nel codice. Visual Studio consente di apportare modifiche temporanee in modo da poter continuare a eseguire il programma.

1. In *Program.cs* fare clic sul margine a sinistra del codice seguente oppure aprire il menu di scelta rapida e scegliere **Punto** di interruzione Inserisci punto di interruzione  >  oppure **premere F9**:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Il cerchio rosso visualizzato indica un punto di interruzione. È possibile usare punti di interruzione per sospendere l'app ed esaminare il codice. È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile.

   ![Screenshot dell'impostazione di un punto di interruzione](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Compilare ed eseguire l'app.

1. Nell'app in esecuzione digitare alcuni valori per il calcolo:

   - Per il primo numero digitare **8** e immetterlo.
   - Per il secondo numero digitare **0** e immetterlo.
   - Per l'operatore, si diverte; digitare **d** e immetterlo.

   L'app sospende la posizione in cui è stato creato il punto di interruzione, indicato dal puntatore giallo a sinistra e dal codice evidenziato. Il codice evidenziato non è ancora stato eseguito.

   ![Screenshot che illustra come raggiungere un punto di interruzione](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Ora, con l'app sospesa, è possibile controllare lo stato dell'applicazione.

## <a name="debug-view-variables"></a>Debug: visualizzare le variabili

1. Nel codice evidenziato passare il mouse su variabili come `cleanNum1` e `op` . I valori correnti per queste variabili ( `8` e , rispettivamente) vengono visualizzati nei suggerimenti `d` dati.

   ![Screenshot della visualizzazione di un suggerimento dati](media/vs-2019/calculator-2-debug-view-datatip.png)

   Durante il debug, verificare se le variabili contengono i valori previsti è spesso fondamentale per la correzione dei problemi.

2. Nel riquadro inferiore esaminare la **finestra** Variabili locali. Se è chiuso, scegliere **Debug**  >  **Windows**  >  **Variabili locali** per aprirlo.

   Nella finestra Variabili locali vengono visualizzati ogni variabile attualmente in ambito, insieme al valore e al tipo.

   ![Screenshot della finestra Variabili locali](media/vs-2019/calculator-2-debug-locals-window.png)

3. Esaminare la **finestra Auto.**

   La finestra Auto è  simile alla finestra Variabili locali, ma mostra le variabili immediatamente precedenti e che segue la riga di codice corrente in cui l'app è sospesa.

   Successivamente, si eseguirà il codice nel debugger un'istruzione alla volta, denominata *esecuzione di istruzioni*.

## <a name="debug-step-through-code"></a>Debug: eseguire il codice un'istruzione alla pagina

1. Premere **F11** (o **Esegui debug** istruzione  >  **in**).

   Usando il comando Esegui istruzione, l'app esegue l'istruzione corrente e passa all'istruzione eseguibile successiva (in genere la riga di codice successiva). Il puntatore giallo a sinistra indica sempre l'istruzione corrente.

   ![Screenshot del comando step-into](media/vs-2019/calculator-2-debug-step-into.png)

   È stato appena illustrato il `DoOperation` metodo nella `Calculator` classe .

1. Per ottenere un'analisi gerarchica del flusso del programma, esaminare la finestra **Stack di** chiamate. Se è chiuso, scegliere **Debug**  >  **Windows**  >  **Stack di chiamate**.

   ![Screenshot dello stack di chiamate](media/vs-2019/calculator-2-debug-call-stack.png)

   Questa visualizzazione mostra il metodo corrente, indicato dal puntatore giallo, e la seconda riga mostra la funzione che lo ha chiamato, dal metodo `Calculator.DoOperation` `Main` in *Program.cs*. La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. Fornisce inoltre l'accesso a molte funzionalità del debugger, ad esempio Vai al codice **sorgente**, dal menu di scelta rapida.

1. Premere **F10** (o **Esegui debug** istruzione) più volte fino a quando  >  l'app non viene sospesa `switch` sull'istruzione.

   ```csharp
   switch (op)
   {
   ```

   Il comando Step Over è simile al comando Step Into, ad eccezione del fatto che se l'istruzione corrente chiama una funzione, il debugger esegue il codice nella funzione chiamata e non sospende l'esecuzione finché la funzione non viene restituita. Eseguire il passaggio è un modo più rapido per spostarsi nel codice se non si è interessati a una funzione specifica.

1. Premere **F10** ancora una volta in modo che l'app si sospende sulla riga di codice seguente.

   ```csharp
   if (num2 != 0)
   {
   ```

   Questo codice verifica la presenza di un caso di divisione per zero. Se l'app continua, genererà un'eccezione generale (un errore), ma si consideri un bug e si voglia eseguire un'altra operazione, ad esempio visualizzare il valore restituito effettivo nella console. Un'opzione è usare una funzionalità del debugger denominata Modifica e continuazione per apportare modifiche al codice e quindi continuare il debug. Tuttavia, verrà illustrato un trucco diverso per modificare temporaneamente il flusso di esecuzione.

## <a name="debug-test-a-temporary-change"></a>Debug: testare una modifica temporanea

1. Selezionare il puntatore giallo, attualmente sospeso `if (num2 != 0)` sull'istruzione, e trascinarlo nell'istruzione seguente.

   ```csharp
   result = num1 / num2;
   ```

   In questo modo, l'app ignora completamente l'istruzione, in modo da poter vedere cosa accade `if` quando si divide per zero.

1. Premere **F10** per eseguire la riga di codice.

1. Passare il `result` puntatore del mouse sulla variabile e vedere che archivia il valore `Infinity` .

   In C# è `Infinity` il risultato quando si divide per zero.

1. Premere **F5** (oppure **Debug Continua**  >  **debug**).

   Il simbolo Infinity viene visualizzato nella console come risultato dell'operazione matematica.

1. Chiudere correttamente l'app usando il comando 'n'.

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
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
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

- [Altre esercitazioni su C#](/dotnet/csharp/tutorials/)
- [Avvio rapido: Creare un'ASP.NET Core Web](../../ide/quickstart-aspnet-core.md)
- [Informazioni sul debug del codice C# in Visual Studio](tutorial-debugger.md)
- Procedura dettagliata su come [creare ed eseguire unit test](../../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Eseguire un programma C#](run-program.md)
- [IntelliSense per C#](../../ide/visual-csharp-intellisense.md)
- [Continuare con la panoramica Visual Studio'IDE](/../visual-studio-ide.md)
