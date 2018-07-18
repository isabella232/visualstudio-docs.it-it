---
title: 'Esercitazione: Eseguire il Debug di codice gestito e nativo (modalità mista)'
description: Informazioni su come eseguire il debug di una DLL nativa da un'app .NET Core o .NET Framework usando il debug in modalità mista
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 1f34f6af0a98e71f5feb910f84e8d67ada051ae9
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057037"
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>Esercitazione: Eseguire il Debug di codice nativo e gestito in Visual Studio

Visual Studio consente di abilitare più di un tipo di debugger durante il debug, che viene chiamato il debug in modalità mista. In questa esercitazione, impostare le opzioni per eseguire il debug di codice nativo e gestito in una singola sessione di debug. Questa esercitazione illustra come eseguire il debug di codice nativo da un'app gestita, ma è anche possibile eseguire l'operazione inversa, e [eseguire il debug di codice gestito da un'app nativa](../debugger/how-to-debug-in-mixed-mode.md). Il debugger supporta anche altri tipi di debug in modalità mista, ad esempio il debug [Python e codice nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) e usando il debugger di script nei tipi di app, ad esempio ASP.NET.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Creare una semplice DLL native
> * Creare una semplice app .NET Core o .NET Framework per chiamare la DLL
> * Avviare il debugger
> * Raggiungere un punto di interruzione nell'app gestita
> * L'istruzione nel codice nativo

## <a name="prerequisites"></a>Prerequisiti

* È necessario installare Visual Studio e il **sviluppo di applicazioni Desktop con C++** carico di lavoro.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* È necessario anche il **sviluppo desktop .NET** carico di lavoro o il **.NET Core lo sviluppo multipiattaforma** carico di lavoro installato, in base al tipo di app usata da creare.

## <a name="create-a-simple-native-dll"></a>Creare una semplice DLL native

1. In Visual Studio, scegliere **File** > **New** > **progetto**.

1. Nel **nuovo progetto** finestra di dialogo, scegliere **Visual C++**, **generali** dalla sezione dei modelli installati, quindi nel riquadro centrale selezionare **progetto vuoto** .

1. Nel **Name** , digitare **Mixed--debug in modalità** e fare clic su **OK**.

    Visual Studio crea il progetto vuoto che viene visualizzato in Esplora soluzioni nel riquadro di destra.

1. In Esplora soluzioni fare doppio clic il **file di origine** nodo in C++ del progetto e quindi scegliere **Add** > **nuovo elemento**e quindi selezionare **C++ file (. cpp)**. Assegnare al file il nome **Mixed Mode.cpp**, quindi scegliere **Add**.

    Visual Studio aggiunge il nuovo file di C++.

1. Copiare il codice seguente nel *Mixed Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. In Esplora soluzioni fare doppio clic il **file di intestazione** nodo in C++ del progetto e quindi scegliere **Add** > **nuovo elemento**e quindi selezionare  **File di intestazione (h)**. Assegnare al file il nome **Mixed Mode.h**, quindi scegliere **Add**.

    Visual Studio aggiunge il nuovo file di intestazione.

1. Copiare il codice seguente nel *Mixed Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. Nella barra degli strumenti di Debug, selezionare una **eseguire il Debug** configuration e **Any CPU** come piattaforma oppure per .NET Core, selezionare **x64** come piattaforma.

    > [!NOTE]
    > In .NET Core, scegliere **x64** come piattaforma. .NET core viene sempre eseguito in modalità a 64 bit in modo che questa operazione è necessaria.

1. In Esplora soluzioni fare doppio clic sul nodo del progetto (**il debug in modalità mista**) e scegliere **proprietà**.

1. Nel **delle proprietà** pagina, scegliere **delle proprietà di configurazione** > **Linker** > **avanzate**, e quindi nel **Nessun punto di ingresso** elenco a discesa, seleziona **NO**. Quindi, applicare le impostazioni.

1. Nel **delle proprietà** pagina, scegliere **le proprietà di configurazione** > **generali**e quindi selezionare **libreria dinamica (. dll)** dal **tipo configurazione** campo. Quindi, applicare le impostazioni.

    ![Passare a una DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Fare clic sul progetto e scegliere **Debug** > **compilare**.

    Il progetto dovrebbe essere compilato senza errori.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Creare un'app .NET Framework o .NET Core semplice per chiamare la DLL

1. In Visual Studio, scegliere **File** > **New** > **progetto**.

1. Scegliere un modello per il codice dell'applicazione.

    Per .NET Framework, nel **nuovo progetto** finestra di dialogo, scegliere **Visual c#**, **Desktop di Windows** dalla sezione dei modelli installati, quindi selezionare il riquadro centrale  **App console (.NET Framework)**.

    Per .NET Core, nelle **nuovo progetto** finestra di dialogo, scegliere **Visual c#**, **.NET Core** dalla sezione dei modelli installati, quindi nel riquadro centrale selezionare  **Console App (.NET Core)**.

1. Nel **Name** , digitare **Mixed_Mode_Calling_App** e fare clic su **OK**.

    Visual Studio crea il progetto console, che viene visualizzato in Esplora soluzioni nel riquadro di destra.

1. Nelle *Program.cs*, sostituire il codice predefinito con il codice seguente:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="configure-mixed-mode-debugging-net-framework"></a>Configurare la modalità mista, debug (.NET Framework)

1. In Esplora soluzioni fare doppio clic su managed **Mixed_Mode_Calling_App** del progetto e scegliere **imposta come progetto di avvio**.

1. Fare doppio clic su managed **Mixed_Mode_Calling_App** del progetto e quindi scegliere **proprietà**, quindi scegliere **Debug** nel riquadro sinistro. Selezionare **Abilita debug codice nativo**e quindi chiudere la pagina delle proprietà per salvare le modifiche.

    ![Abilitare il debug in modalità mista](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Configurare la modalità mista, debug (.NET Core)

Nella maggior parte delle versioni di Visual Studio 2017, è necessario abilitare il debug in modalità mista per il codice nativo in un'app .NET Core usando il *launchsettings. JSON* del file anziché la **proprietà** pagina. Per tenere traccia degli aggiornamenti dell'interfaccia utente per questa funzionalità, vedere questo [problema di GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Aprire il *launchsettings. JSON* del file nei *proprietà* cartella. Per impostazione predefinita, è possibile trovare il file in questa posizione.

    *C:\Users\<username > \source\repos\Mixed_Mode_Calling_App\Properties*

    Se il file non è presente, aprire le proprietà del progetto (fare doppio clic su managed **Mixed_Mode_Calling_App** del progetto in Esplora soluzioni e selezionare **proprietà**). Apportare una modifica temporanea nel **Debug** scheda e compilare il progetto. Annullare le modifiche apportate.

1. Nel *lauchsettings.json* , aggiungere la seguente proprietà:

    ```csharp
    "nativeDebugging": true
    ```

    Quindi, ad esempio, il file potrebbe essere simile al seguente:

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

1. Nel progetto c#, aprire *Program.cs* e impostare un punto di interruzione nella riga di codice seguente facendo clic nel margine sinistro:

    ```csharp
    int result = Multiply(7, 7);
    ```

    Viene visualizzato un cerchio rosso sul margine sinistro per indicare di aver impostato il punto di interruzione.

1. Premere **F5** (**Debug** > **Avvia debug**) per avviare il debugger.

    Il debugger sospende sul punto di interruzione impostato. Una freccia gialla indica in cui il debugger è attualmente sospesa.

## <a name="step-into-native-code"></a>L'istruzione nel codice nativo

1. Durante la pausa dell'app gestita, premere **F11** (**Debug** > **Esegui istruzione**).

    Si apre il file di intestazione con il codice nativo e visualizzato la freccia gialla in cui il debugger viene sospeso.

    ![L'istruzione nel codice nativo](../debugger/media/mixed-mode-step-into-native-code.png)

    A questo punto, è possibile eseguire le operazioni set e raggiungere punti di interruzione e ispezionare le variabili.

1. Passare il mouse sulle variabili per vedere il loro valore.

1. Esaminare i **Auto** e **variabili locali** windows per visualizzare una variabile e i relativi valori.

    Durante la pausa del debugger, è possibile usare altre funzionalità del debugger, ad esempio la **Watch** finestra e il **Stack di chiamate** finestra.

1. Premere **F11** nuovamente per passare la riga di un debugger.

1. Premere **MAIUSC+F11** (**Debug** > **Esci da istruzione /**) per continuare l'esecuzione di app e sospendere nuovamente nell'app gestite.

1. Premere **F5** per continuare con l'esecuzione dell'app.

    La procedura è stata completata. È stata completata l'esercitazione sul debug in modalità mista.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato illustrato come eseguire il debug di codice nativo da un'app gestita, consentendo il debug in modalità mista. Per una panoramica delle altre funzionalità di debug, vedere l'articolo seguente:

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
