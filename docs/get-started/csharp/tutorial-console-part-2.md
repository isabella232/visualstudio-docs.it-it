---
title: 'Esercitazione: estendere una semplice app console C#'
description: Informazioni dettagliate su come sviluppare un'app console C# in Visual Studio.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aae83c43a106fd68b03a83124ad2ddcea4652c8d
ms.sourcegitcommit: c620d59578db1b89f80e64ae04b4898bc4ab292d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377172"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>Esercitazione: estendere una semplice app console C#

Questa esercitazione illustra come usare Visual Studio per estendere l'app console creata nella prima parte. Verranno illustrate alcune delle funzionalità di Visual Studio che consentono di migliorare la produttività degli sviluppatori, ad esempio l'utilizzo di funzionalità avanzate dell'editor e il debug.

Se è stata appena completata la [prima parte](tutorial-console.md) di questa serie, è già presente l'app console per la calcolatrice.  Per ignorare la parte 1, è possibile iniziare aprendo il progetto da un repository GitHub. L'app del calcolatore C# si trova nel [repository vs-tutorial-Samples](https://github.com/MicrosoftDocs/vs-tutorial-samples), quindi è possibile seguire la procedura descritta in [esercitazione: aprire un progetto da un repository](../tutorial-open-project-from-repo.md) per iniziare.

## <a name="add-a-new-project"></a>Aggiungere un nuovo progetto

Il codice del mondo reale implica la collaborazione di molti progetti in una soluzione. A questo punto, aggiungere un altro progetto all'app Calculator. Si tratta di una libreria di classi che fornisce alcune funzioni del calcolatore.

1. In Visual Studio è possibile usare il **file**di comando di menu di primo livello  >  **Aggiungi**  >  **nuovo progetto** per aggiungere un nuovo progetto, ma è anche possibile fare clic con il pulsante destro del mouse sul nome del progetto esistente (denominato "nodo progetto") e aprire il menu di scelta rapida del progetto (o menu di scelta rapida). Questo menu di scelta rapida contiene molti modi per aggiungere funzionalità ai progetti. Quindi, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni**e scegliere **Aggiungi**  >  **nuovo progetto**.

1. Scegliere la libreria di classi del modello di progetto C# **(.NET standard)**.

   ![Screenshot della selezione del modello di progetto della libreria di classi](media/vs-2019/calculator2-add-project-dark.png)

1. Digitare il nome del progetto **CalculatorLibrary**e scegliere **Crea**. Visual Studio crea il nuovo progetto e lo aggiunge alla soluzione.

   ![Screenshot di Esplora soluzioni con il progetto di libreria di classi CalculatorLibrary aggiunto](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. Anziché *Class1.cs*, rinominare il file **CalculatorLibrary.cs**. È possibile fare clic sul nome in **Esplora soluzioni** per rinominarlo oppure fare clic con il pulsante destro del mouse e scegliere **Rinomina**oppure premere il tasto **F2** .

   È possibile che venga chiesto se si desidera rinominare tutti i riferimenti a `Class1` nel file. Non importa come si risponde, perché il codice verrà sostituito in un passaggio successivo.

1. È ora necessario aggiungere un riferimento al progetto, in modo che il primo progetto possa usare le API esposte dalla nuova libreria di classi.  Fare clic con il pulsante destro del mouse sul nodo **riferimenti** nel primo progetto e scegliere **Aggiungi riferimento al progetto**.

   ![Screenshot della voce di menu Aggiungi riferimento al progetto](media/vs-2019/calculator2-add-project-reference-dark.png)

   Verrà visualizzata la finestra di dialogo **Gestione riferimenti**. Questa finestra di dialogo consente di aggiungere riferimenti ad altri progetti, nonché ad assembly e DLL COM necessari per i progetti.

   ![Screenshot della finestra di dialogo Gestione riferimenti](media/vs-2019/calculator2-ref-manager-dark.png)

1. Nella finestra di dialogo **Gestione riferimenti** selezionare la casella di controllo per il progetto **CalculatorLibrary** e scegliere **OK**.  Il riferimento al progetto viene visualizzato in un nodo **progetti** in **Esplora soluzioni**.

   ![Screenshot di Esplora soluzioni con riferimento al progetto](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. In *Program.cs*selezionare la `Calculator` classe e tutto il relativo codice e premere **CTRL + X** per tagliarlo da Program.cs. In **CalculatorLibrary**, in *CalculatorLibrary.cs*, incollare il codice nello `CalculatorLibrary` spazio dei nomi. Quindi, fare in modo che la classe Calculator la `public` esponga all'esterno della libreria. Il codice in *CalculatorLibrary.cs* dovrebbe essere simile al codice seguente:

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

1. Il primo progetto ha un riferimento, ma viene visualizzato un errore che segnala che la chiamata Calculator. DoOperation non viene risolta. Questo perché CalculatorLibrary si trova in uno spazio dei nomi Difference, quindi Aggiungi `CalculatorLibrary` spazio dei nomi per un riferimento completo.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   Provare ad aggiungere invece una direttiva using all'inizio del file:

   ```csharp
   using CalculatorLibrary;
   ```

   Questa modifica dovrebbe consentire di rimuovere lo spazio dei nomi CalculatorLibrary dal sito di chiamata, ma ora esiste un'ambiguità. `Calculator`La classe è in CalculatorLibrary o è Calculator lo spazio dei nomi?  Per risolvere l'ambiguità, rinominare lo spazio dei nomi `CalculatorProgram` .

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>Librerie .NET di riferimento: scrivere in un log

1. Si supponga ora di voler aggiungere un log di tutte le operazioni e di scriverlo in un file di testo. `Trace`Questa funzionalità è fornita dalla classe .NET. È utile anche per le tecniche di debug di stampa di base.  La classe Trace si trova in System. Diagnostics, quindi iniziare aggiungendo una direttiva using:

   ```csharp
   using System.Diagnostics;
   ```

1. Esaminando il modo in cui viene utilizzata la classe Trace, è necessario utilizzare un riferimento per la classe associata a un oggetto FileStream. Ciò significa che il calcolatore funzionerebbe meglio come oggetto, quindi si aggiungerà un costruttore.

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

1. Ed è necessario modificare il metodo statico `DoOperation` in un metodo del membro.  Si aggiungerà anche l'output a ogni calcolo per il log, in modo che DoOperation appaia come il codice seguente:

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

1. Tornando a Program.cs, la chiamata statica viene contrassegnata con un ondulato rosso. Per risolvere il problema, creare una `calculator` variabile aggiungendo la riga seguente subito prima del ciclo while:

   ```csharp
   Calculator calculator = new Calculator();
   ```

   E modificare il sito di chiamata per `DoOperation` come segue:

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. Eseguire di nuovo il programma e, al termine, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri cartella in Esplora file**, quindi passare alla cartella di output in Esplora file. Potrebbe essere *bin/debug/netcoreapp 3.1*e aprire il file *Calculator. log* .

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>Aggiungere un pacchetto NuGet: scrivere in un file JSON

1. Si supponga ora di voler restituire le operazioni in formato JSON, un formato popolare e portatile per l'archiviazione dei dati degli oggetti. Per implementare questa funzionalità, è necessario fare riferimento al pacchetto NuGet Newtonsoft.Json. I pacchetti NuGet sono il veicolo principale per la distribuzione delle librerie di classi .NET. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo **riferimenti** per il progetto CalculatorLibrary e scegliere **Gestisci pacchetti NuGet**.

   ![Screenshot della gestione dei pacchetti NuGet dal menu di scelta rapida](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   Verrà aperto Gestione pacchetti NuGet.

   ![Screenshot di Gestione pacchetti NuGet](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Cercare Newtonsoft.Jsnel pacchetto e scegliere **Installa**.

   ![Screenshot delle informazioni sul pacchetto NuGet Newtonsoft](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   Il pacchetto viene scaricato e aggiunto al progetto e viene visualizzata una nuova voce nel nodo riferimenti in **Esplora soluzioni**.

1. Aggiungere una direttiva using per il Newtonsoft.Jsnel pacchetto all'inizio di *CalculatorLibrary.cs*.

   ```csharp
   using Newtonsoft.Json;
   ```

1. A questo punto, sostituire il costruttore per Calculator con il codice seguente e creare l'oggetto membro JsonWriter:

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

1. È necessario aggiungere un metodo per completare la sintassi JSON dopo che l'utente ha eseguito l'immissione dei dati dell'operazione.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. In *Program.cs*aggiungere una chiamata a Finish alla fine.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. Compilare ed eseguire l'app. dopo aver completato l'immissione di alcune operazioni, chiudere l'app correttamente usando il comando ' n'.  A questo punto, aprire il consolelog.jsnel file e dovrebbe essere visualizzato un risultato simile al seguente:

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

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Altre esercitazioni su C#](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Continua con la panoramica dell'IDE di Visual Studio](/../visual-studio-ide.md)

## <a name="see-also"></a>Vedere anche

* [IntelliSense per C#](../../ide/visual-csharp-intellisense.md)
* [Informazioni sul debug del codice C# in Visual Studio](tutorial-debugger.md)
