---
title: Introduzione alle app console C# in Visual Studio
description: Informazioni dettagliate su come creare un'app console C# in Visual Studio.
ms.custom: ''
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 3450572e4cf4959530599c5eea9efb3168485b58
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244372"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Esercitazione: Introduzione a un'app console C# in Visual Studio

In questa esercitazione per C# si userà Visual Studio per creare ed eseguire un'app console ed esplorare alcune funzionalità dell'[ambiente di sviluppo integrato (IDE, Integrated Development Environment) di Visual Studio](visual-studio-ide.md).

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa, creare un progetto di applicazione C#. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

1. Aprire Visual Studio 2017.

2. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al file il nome *CalculateThis*.

   ![Modello di progetto Console App (.NET Core) nella finestra di dialogo Nuovo progetto dell'IDE di Visual Studio](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Aggiungere un gruppo di lavoro (facoltativo)

Se il modello di progetto **Console App (.NET Core)** non è visualizzato, è possibile ottenerlo aggiungendo il carico di lavoro **Sviluppo multipiattaforma .NET Core**. È possibile aggiungere questo carico di lavoro in uno dei due modi seguenti, a seconda degli aggiornamenti di Visual Studio 2017 installati nel computer.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opzione 1: usare la finestra di dialogo Nuovo progetto

1. Fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

   ![Fare clic sul collegamento Apri il programma di installazione di Visual Studio dalla finestra di dialogo Nuovo progetto](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

   ![Carico di lavoro Sviluppo multipiattaforma .NET Core nel programma di installazione di Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opzione 2: usare la barra del menu Strumenti

1. Chiudere la finestra di dialogo **Nuovo progetto** e sulla barra dei menu in alto scegliere **Strumenti** > **Ottieni strumenti e funzionalità**.

1. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

## <a name="create-a-c-console-calculator-app"></a>Creare un'app "calcolatore console C#"

1. Dopo aver creato l'**applicazione console C#**, immettere o incollare il codice seguente nell'editor di codice:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

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
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   Il codice visualizzato dopo `static void Main(string[] args)` sarà simile allo screenshot seguente:

   ![Editor di codice che mostra il calcolatore console C#](../ide/media/csharp-console-calculator-code.png)

1. Scegliere **Calculator** per eseguire il programma oppure premere **F5**.

   ![Scegliere il pulsante Calculator per eseguire l'app dalla barra degli strumenti](../ide/media/csharp-console-calculator-button.png)

1. Visualizzare l'app nella finestra della console. Se si seguono le istruzioni, l'app sarà simile allo screenshot seguente:

    ![Finestra della console che mostra l'app Calculator, che include le istruzioni sulle azioni da eseguire.](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Chiudere l'app

1. Premere un tasto qualsiasi per chiudere l'app calcolatore.

1. Chiudere il riquadro **Output** in Visual Studio.

   ![Chiudere il riquadro Output in Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Chiudere Visual Studio.

## <a name="quick-answers-faq"></a>Domande frequenti con risposta rapida

Ecco una rapida serie di domande frequenti per evidenziare alcuni concetti chiave.

### <a name="what-is-c"></a>Che cos'è C#?

C# è un linguaggio di programmazione che viene eseguito in .NET Framework e .NET Core. Con C# è possibile creare applicazioni Windows, applicazioni server client, applicazioni database, servizi Web XML, componenti distribuiti e altro ancora.

### <a name="what-is-visual-studio"></a>Che cos'è Visual Studio?

Visual Studio è una suite integrata per lo sviluppo di strumenti di produttività per gli sviluppatori. Si può immaginare Visual Studio come un programma utilizzabile per creare programmi e applicazioni.

### <a name="what-is-a-console-app"></a>Che cos'è un'app console?

Un'app console riceve input e visualizza output in una finestra della riga di comando, detta anche console.

### <a name="what-is-net-core"></a>Informazioni su .NET Core

.NET Core è il passaggio successivo nell'evoluzione di .NET Framework. Mentre .NET Framework consentiva di condividere codice tra linguaggi di programmazione diversi, .NET Core aggiunge la possibilità di condividere codice tra piattaforme diverse. E, ciliegina sulla torta, è open source.

.NET Framework e .NET Core includono entrambi librerie di funzionalità precompilate. Includono anche un Common Language Runtime (CLR), che opera come macchina virtuale in cui eseguire il codice.

## <a name="next-steps"></a>Passaggi successivi

L'esercitazione è stata completata. Per altre informazioni, continuare con le esercitazioni seguenti.

> [!div class="nextstepaction"]
> [Esercitazioni su C#](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Vedere anche

* [Esercitazione video C# Fundamentals for Absolute Beginners (Concetti di base su C# per principianti)](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
