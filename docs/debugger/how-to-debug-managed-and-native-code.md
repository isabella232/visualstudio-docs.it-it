---
title: 'Esercitazione: Il Debug del codice gestito e nativo | Documenti Microsoft'
description: Informazioni su come eseguire il debug di una DLL nativa da un'app .NET Framework o .NET Core
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
ms.openlocfilehash: 548b86406ba36a6f46a2dfb3d4d894b5621c298c
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>Esercitazione: Il Debug del codice gestito e nativo in Visual Studio

Visual Studio consente di abilitare più di un tipo di debugger durante il debug, che viene chiamato il debug in modalità mista. In questa esercitazione, impostare le opzioni per eseguire il debug di codice nativo e gestito in un'unica sessione di debug. Questa esercitazione viene illustrato come eseguire il debug di codice nativo da un'app gestita, ma è anche possibile eseguire l'operazione inversa, e [eseguire il debug di codice gestito da un'applicazione nativa](../debugger/how-to-debug-in-mixed-mode.md). Il debugger supporta anche altri tipi di debug in modalità mista, ad esempio il debug [Python e codice nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) e utilizzando il debugger di script nei tipi di app, ad esempio ASP.NET.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Creare una DLL nativa semplice
> * Creare una semplice app .NET Framework o .NET Core per chiamare la DLL
> * Avviare il debugger
> * Raggiungere un punto di interruzione nell'app gestite
> * Passaggio in codice nativo

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio installato e il **lo sviluppo Desktop con C++** carico di lavoro.

    Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* È necessario disporre anche il **lo sviluppo desktop .NET** carico di lavoro o il **.NET Core sviluppo App per multipiattaforma** carico di lavoro installato, a seconda del tipo di quali app da creare.

## <a name="create-a-simple-native-dll"></a>Creare una DLL nativa semplice

1. In Visual Studio, scegliere **File** > **New** > **progetto**.

1. Nel **nuovo progetto** finestra di dialogo, scegliere **Visual C++**, **generale** dalla sezione dei modelli installati, quindi nel riquadro centrale selezionare **progetto vuoto** .

1. Nel **nome** , digitare **il debug in modalità mista** e fare clic su **OK**.

    Visual Studio crea il progetto vuoto, che viene visualizzato in Esplora soluzioni nel riquadro di destra.

1. In Esplora soluzioni fare doppio clic sul **file di origine** nodo in C++ del progetto e quindi scegliere **Aggiungi** > **nuovo elemento**, quindi selezionare **C++ file (. cpp)**. Assegnare al file il nome **Mixed Mode.cpp**, quindi scegliere **Add**.

    Visual Studio aggiungerà il nuovo file di C++.

1. Copiare il codice seguente nel *Mixed Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. In Esplora soluzioni fare doppio clic sul **file di intestazione** nodo in C++ del progetto e quindi scegliere **Aggiungi** > **nuovo elemento**, quindi selezionare  **File di intestazione (h)**. Assegnare al file il nome **Mixed Mode.h**, quindi scegliere **Add**.

    Visual Studio aggiungerà il nuovo file di intestazione.

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

1. Nella barra degli strumenti di Debug, selezionare una **Debug** configurazione e **qualsiasi CPU** come piattaforma di oppure, per .NET Core, selezionare **x64** come la piattaforma.

    > [!NOTE]
    > In .NET Core, scegliere **x64** come la piattaforma. .NET core sempre in esecuzione in modalità a 64 bit in modo che questa operazione è necessaria.

1. In Esplora soluzioni, fare clic sul nodo del progetto (**il debug in modalità mista**) e scegliere **proprietà**.

1. Nel **delle proprietà** pagina, scegliere **delle proprietà di configurazione** > **Linker** > **avanzate**, e quindi nella **Nessun punto di ingresso** elenco a discesa, seleziona **n**. Quindi applicare le impostazioni.

1. Nel **proprietà** pagina, scegliere **le proprietà di configurazione** > **generale**, quindi selezionare **libreria dinamica (. dll)** dal **tipo di configurazione** campo. Quindi applicare le impostazioni.

    ![Passare a una DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Fare clic sul progetto e scegliere **Debug** > **compilare**.

    Il progetto dovrebbe essere compilato senza errori.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Creare una semplice app .NET Framework o .NET Core per chiamare la DLL

1. In Visual Studio, scegliere **File** > **New** > **progetto**.

1. Scegliere un modello per il codice dell'applicazione.

    Per .NET Framework, nelle **nuovo progetto** finestra di dialogo, scegliere **Visual c#**, **Windows Desktop classico** dalla sezione dei modelli installati, quindi nel riquadro centrale Selezionare **applicazione Console (.NET Framework)**.

    Per .NET Core nel **nuovo progetto** finestra di dialogo, scegliere **Visual c#**, **.NET Core** dalla sezione dei modelli installati, quindi nel riquadro centrale selezionare  **Console di App (.NET Core)**.

1. Nel **nome** , digitare **Mixed_Mode_Calling_App** e fare clic su **OK**.

    Visual Studio crea il progetto console, che viene visualizzato in Esplora soluzioni nel riquadro di destra.

1. In *Program.cs*, sostituire il codice predefinito con il codice seguente:

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

## <a name="configure-mixed-mode-debugging-net-framework"></a>Configurare la modalità mista di debug (.NET Framework)

1. In Esplora soluzioni fare doppio clic su gestito **Mixed_Mode_Calling_App** del progetto e scegliere **imposta come progetto di avvio**.

1. Fare doppio clic su gestito **Mixed_Mode_Calling_App** del progetto e quindi scegliere **proprietà**, quindi scegliere **Debug** nel riquadro sinistro. Selezionare **Abilita debug codice nativo**e quindi chiudere la pagina delle proprietà per salvare le modifiche.

    ![Abilitare il debug in modalità mista](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Configurare la modalità mista (.NET Core) di debug

Nella maggior parte delle versioni di Visual Studio 2017, è necessario abilitare il debug in modalità mista per il codice nativo in un'app .NET Core usando il *launchSettings.json* file anziché il **proprietà** pagina. Per tenere traccia degli aggiornamenti dell'interfaccia utente per questa funzionalità, vedere questo [problema GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Aprire la *launchSettings.json* del file nel *proprietà* cartella. Per impostazione predefinita, è possibile trovare il file in questa posizione.

    *C:\Users\<nomeutente > \source\repos\Mixed_Mode_Calling_App\Properties*

    Se il file non è presente, aprire le proprietà del progetto (fare doppio clic su gestito **Mixed_Mode_Calling_App** sul progetto in Esplora soluzioni e selezionare **proprietà**). Apportare una modifica temporanea nel **Debug** scheda e compilare il progetto. Ripristinare le modifiche apportate.

1. Nel *lauchsettings.json* file, aggiungere la proprietà seguente:

    ```
    "nativeDebugging": true
    ```
    
    In tal caso, ad esempio, il file potrebbe essere simile quanto segue:
    
    ```
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

1. Nel progetto c#, aprire *Program.cs* e impostare un punto di interruzione nella riga seguente di codice facendo clic sul margine sinistro:

    ```csharp
    int result = Multiply(7, 7);
    ```

    Verrà visualizzato un cerchio rosso nel margine sinistro per indicare di aver impostato il punto di interruzione.

1. Premere **F5** (**Debug** > **Avvia debug**) per avviare il debugger.

    Il debugger sospende del punto di interruzione impostati. Una freccia gialla indica dove il debugger è attualmente sospesa.

## <a name="step-into-native-code"></a>Passaggio in codice nativo

1. Durante la sospensione di app gestita, premere **F11** (**Debug** > **Esegui istruzione**).

    Apre il file di intestazione con il codice nativo e si noterà la freccia gialla in cui il debugger ha sospeso.

    ![Passaggio in codice nativo](../debugger/media/mixed-mode-step-into-native-code.png)

    A questo punto, è possibile eseguire operazioni come impostare e raggiungere punti di interruzione e controllare le variabili.

1. Soffermare le variabili per visualizzare i relativi valori.

1. Esaminare i **Auto** e **variabili locali** windows per visualizzare una variabile e i relativi valori.

    Durante la pausa nel debugger, è possibile usare altre funzionalità del debugger, ad esempio il **Watch** finestra e il **Stack di chiamate** finestra.

1. Premere **F11** nuovamente per spostare la riga di un debugger.

1. Premere **MAIUSC+F11** (**Debug** > **Esci**) per continuare l'esecuzione di app e sospendere nuovamente nell'app gestite.

1. Premere **F5** per continuare con l'esecuzione dell'app.

    La procedura è stata completata. È stata completata l'esercitazione sul debug in modalità mista.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato descritto come eseguire il debug di codice nativo da un'app gestita abilitando il debug in modalità mista. Per una panoramica delle altre funzionalità di debug, vedere l'articolo seguente:

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)