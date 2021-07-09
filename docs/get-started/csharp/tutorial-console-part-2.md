---
title: 'Esercitazione: Estendere una semplice app console C#'
description: Informazioni dettagliate su come sviluppare un Visual Studio app console C#.
ms.custom: vs-acquisition, get-started
ms.date: 04/15/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84a79015dc4b1147f078b0a970df52c553189c92
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549498"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Esercitazione: Estendere una semplice app console C#

In questa esercitazione si apprenderà come usare Visual Studio per estendere l'app console creata nella prima parte. Si apprenderanno alcune delle funzionalità di Visual Studio necessarie per lo sviluppo giornaliero, ad esempio la gestione di più progetti e il riferimento a pacchetti di terze parti.

Se è stata appena completata la [prima parte di](tutorial-console.md) questa serie, si dispone già dell'app console Calculator.  Per ignorare la parte 1, è possibile iniziare aprendo il progetto da un GitHub di lavoro. L'app Calcolatrice C# si trova nel [repo vs-tutorial-samples,](https://github.com/MicrosoftDocs/vs-tutorial-samples)quindi è sufficiente seguire i passaggi descritti in Esercitazione: Aprire un progetto da un [repo](../tutorial-open-project-from-repo.md) per iniziare.

## <a name="add-a-new-project"></a>Aggiungere un nuovo progetto

Il codice reale implica la collaborazione di molti progetti in una soluzione. Aggiungere ora un altro progetto all'app Calculator. Si tratta di una libreria di classi che fornisce alcune delle funzioni della calcolatrice.

1. In Visual Studio è possibile usare il comando di menu di primo livello **File** Aggiungi nuovo Project per aggiungere un nuovo progetto, ma è anche possibile fare clic con il pulsante destro del mouse sul nome del progetto esistente  >    >   (denominato "nodo del progetto") e aprire il menu di scelta rapida (o il menu di scelta rapida) del progetto. Questo menu di scelta rapida contiene molti modi per aggiungere funzionalità ai progetti. Fare quindi clic con il pulsante destro del mouse sul nodo del **progetto Esplora soluzioni** e scegliere Aggiungi  >  **nuovo Project**.

1. Scegliere il modello di progetto C# **Libreria di classi (.NET Standard)**.

   ![Screenshot della selezione del modello di progetto Libreria di classi](media/vs-2019/calculator2-add-project-dark.png)

1. Digitare il nome del **progetto CalculatorLibrary** e scegliere **Crea.** Anche in questo caso, scegliere .NET 3.1 quando richiesto. Visual Studio crea il nuovo progetto e lo aggiunge alla soluzione.

   ![Screenshot della Esplora soluzioni con il progetto libreria di classi CalculatorLibrary aggiunto](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Invece di avere *Class1.cs*, rinominare il file **CalculatorLibrary.cs**. È possibile fare clic sul nome nel **Esplora soluzioni** rinominarlo oppure fare clic con il pulsante destro del mouse e scegliere **Rinomina** oppure **premere F2.**

   Potrebbe essere richiesto se si desidera rinominare i riferimenti `Class1` a nel file . Non è importante come rispondere, perché il codice verrà sostituito in un passaggio futuro.

1. È ora necessario aggiungere un riferimento al progetto, in modo che il primo progetto possa usare le API esposte dalla nuova libreria di classi.  Fare clic con il pulsante destro **del mouse sul** nodo Dipendenze nel primo progetto e scegliere Project Riferimento **.**

   ![Screenshot della voce di menu Project riferimenti](media/vs-2019/calculator2-add-project-reference-dark.png)

   Verrà visualizzata la finestra di dialogo **Gestione riferimenti**. Questa finestra di dialogo consente di aggiungere riferimenti ad altri progetti, nonché ad assembly e DLL COM necessari per i progetti.

   ![Screenshot della finestra di dialogo Gestione riferimenti](media/vs-2019/calculator2-ref-manager-dark.png)

1. Nella finestra **di dialogo Gestione** riferimenti selezionare la casella di controllo per il progetto **CalculatorLibrary** e scegliere **OK.**  Il riferimento al progetto viene visualizzato sotto un **nodo Progetti** in **Esplora soluzioni**.

   ![Screenshot dell'Esplora soluzioni con riferimento al progetto](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. In *Program.cs* selezionare la classe e tutto il relativo `Calculator` codice e premere **CTRL+X** per tagliarla da Program.cs. Quindi in **CalculatorLibrary** in *CalculatorLibrary.cs incollare* il codice nello spazio dei `CalculatorLibrary` nomi . Impostare quindi la classe Calculator per `public` esporla all'esterno della libreria. Il codice in *CalculatorLibrary.cs* dovrebbe ora essere simile al codice seguente:

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

1. Il primo progetto contiene un riferimento, ma verrà visualizzato un errore che la chiamata a Calculator.DoOperation non viene risolta. Questo perché CalculatorLibrary si trova in uno spazio dei nomi diverso, quindi aggiungere `CalculatorLibrary` lo spazio dei nomi per un riferimento completo.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Provare ad aggiungere una direttiva using all'inizio del file:

   ```csharp
   using CalculatorLibrary;
   ```

   Questa modifica dovrebbe consentire di rimuovere lo spazio dei nomi CalculatorLibrary dal sito di chiamata, ma ora esiste un'ambiguità. La `Calculator` classe in CalculatorLibrary o Calculator è lo spazio dei nomi ?  Per risolvere l'ambiguità, rinominare lo spazio dei nomi `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Fare riferimento alle librerie .NET: scrivere in un log

1. Si supponga di voler aggiungere un log di tutte le operazioni e scriverlo in un file di testo. La classe .NET `Trace` fornisce questa funzionalità. È utile anche per le tecniche di debug di stampa di base.  La classe Trace si trova in System.Diagnostics e saranno necessarie System.IO classi come , quindi iniziare aggiungendo le direttive using all'inizio `StreamWriter` di *CalculatorLibrary.cs:*

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

1. Ed è necessario modificare il metodo statico `DoOperation` in un metodo membro, quindi rimuovere la parola `static` chiave .  Aggiungere anche l'output a ogni calcolo per il log, in modo che DoOperation sia simile al codice seguente:

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

1. Ora di nuovo in *Program.cs,* la chiamata statica è contrassegnata con un rosso ondulato. Per risolvere il problema, creare `calculator` una variabile aggiungendo la riga seguente subito prima del ciclo `while (!endApp)` :

   ```csharp
   Calculator calculator = new Calculator();
   ```

   Modificare il sito di chiamata per come indicato di seguito, in modo che faccia riferimento all'oggetto denominato in minuscolo, rendendo in tal modo la chiamata a un membro anziché una chiamata `DoOperation` `calculator` a un metodo statico:

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

A questo punto, *CalculatorLibrary.cs* dovrebbe essere simile al seguente:

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

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Aggiungere un pacchetto NuGet: scrivere in un file JSON

1. Si supponga ora di voler eseguire l'output delle operazioni in un formato JSON, un formato comune e portabile per l'archiviazione dei dati degli oggetti. Per implementare questa funzionalità, è necessario fare riferimento al NuGet di Newtonsoft.Jssu. NuGet pacchetti sono il veicolo principale per la distribuzione delle librerie di classi .NET. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Dipendenze** per il progetto CalculatorLibrary e scegliere Gestisci NuGet **progetto.**

   ![Screenshot di Gestisci NuGet pacchetti nel menu di scelta rapida](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Verrà NuGet Gestione pacchetti la finestra di dialogo.

   ![Screenshot di Gestione pacchetti NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Cercare Newtonsoft.Jsnel pacchetto e scegliere **Installa.**

   ![Screenshot delle informazioni sul pacchetto NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Il pacchetto viene scaricato e aggiunto al progetto e viene visualizzata una nuova voce nel nodo Riferimenti in **Esplora soluzioni**.

1. Aggiungere una direttiva using per il System.IO e Newtonsoft.Jsnel pacchetto all'inizio di *CalculatorLibrary.cs.*

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

1. Compilare ed eseguire l'app e, dopo aver immesso alcune operazioni, chiudere correttamente l'app usando il comando "n".  A questo punto, aprire calculatorlog.jsnel file . Verrà visualizzato un messaggio simile al seguente:

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

Il debugger Visual Studio è un potente strumento che consente di eseguire il codice un'istruzione alla volta, per trovare il punto esatto in cui si è fatto un errore di programmazione. È quindi possibile comprendere quali correzioni è necessario apportare nel codice. Visual Studio consente di apportare modifiche temporanee per poter continuare a eseguire il programma.

1. In *Program.cs* fare clic sul margine a sinistra del codice seguente oppure aprire il menu di scelta rapida e scegliere Punto di interruzione Inserisci punto di interruzione oppure  >  premere **F9**:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Il cerchio rosso visualizzato indica un punto di interruzione. È possibile usare i punti di interruzione per sospendere l'app ed esaminare il codice. È possibile impostare un punto di interruzione in qualsiasi riga di codice eseguibile.

   ![Screenshot dell'impostazione di un punto di interruzione](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. Compilare ed eseguire l'app.

1. Nell'app in esecuzione digitare alcuni valori per il calcolo:

   - Per il primo numero digitare **8** e immetterlo.
   - Per il secondo numero digitare **0** e immetterlo.
   - Per l'operatore , diamo un po' di tempo. digitare **d** e immetterlo.

   L'app sospende la posizione in cui è stato creato il punto di interruzione, indicato dal puntatore giallo a sinistra e dal codice evidenziato. Il codice evidenziato non è ancora stato eseguito.

   ![Screenshot del clic su un punto di interruzione](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   Ora, con l'app sospesa, è possibile controllare lo stato dell'applicazione.

## <a name="debug-view-variables"></a>Debug: visualizzare le variabili

1. Nel codice evidenziato passare il mouse su variabili come `cleanNum1` e `op` . Vengono visualizzati i valori correnti per queste variabili ( `8` e , rispettivamente), visualizzati in Suggerimenti `d` dati.

   ![Screenshot della visualizzazione di un suggerimento dati](media/vs-2019/calculator-2-debug-view-datatip.png)

   Durante il debug, verificare se le variabili contengono i valori previsti è spesso fondamentale per risolvere i problemi.

2. Nel riquadro inferiore esaminare la **finestra** Variabili locali. Se è chiuso, scegliere **Debug**  >  **Windows**  >  **Variabili locali** per aprirlo.

   Nella finestra Variabili locali vengono visualizzati ogni variabile attualmente in ambito, insieme al valore e al tipo.

   ![Screenshot della finestra Variabili locali](media/vs-2019/calculator-2-debug-locals-window.png)

3. Esaminare la **finestra Auto.**

   La finestra Auto è  simile alla finestra Variabili locali, ma mostra le variabili immediatamente che precedono e segue la riga di codice corrente in cui l'app è sospesa.

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

   Il simbolo Infinito viene visualizzato nella console come risultato dell'operazione matematica.

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

L'esercitazione è stata completata. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Altre esercitazioni su C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Continuare con la panoramica Visual Studio'IDE](/../visual-studio-ide.md)

## <a name="see-also"></a>Vedi anche

- [IntelliSense per C#](../../ide/visual-csharp-intellisense.md)
- [Informazioni sul debug del codice C# in Visual Studio](tutorial-debugger.md)
