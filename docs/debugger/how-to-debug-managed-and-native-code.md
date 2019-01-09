---
title: 'Esercitazione: eseguire il debug di codice C# e C++ (modalità mista)'
description: Informazioni su come eseguire il debug di una DLL nativa da un'app .NET Core o .NET Framework con il debug in modalità mista
ms.custom: seodec18
ms.date: 11/02/2018
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
ms.openlocfilehash: 475160a7ba08cb334eeb26be26731deea547f6ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920868"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Esercitazione: eseguire il debug di C# e C++ nella stessa sessione di debug

Visual Studio consente di abilitare più di un tipo di debugger in una sessione di debug, chiamata debug in modalità mista. In questa esercitazione viene illustrato come eseguire il debug di codice nativo e gestito in una singola sessione di debug. 

Questa esercitazione illustra come eseguire il debug di codice nativo da un'app gestita, ma è anche possibile [eseguire il debug di codice gestito da un'app nativa](../debugger/how-to-debug-in-mixed-mode.md). Il debugger supporta anche altri tipi di debug in modalità mista, ad esempio il debug [di codice Python e nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) e l'uso del debugger di script in tipi di app come ad esempio ASP.NET.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Creare una semplice DLL nativa
> * Creare una semplice app .NET Core o .NET Framework per chiamare la DLL
> * Configurare il debug in modalità mista
> * Avviare il debugger
> * Raggiungere un punto di interruzione nell'app gestita
> * Eseguire l'istruzione del codice nativo

## <a name="prerequisites"></a>Prerequisiti

È necessario avere installato Visual Studio, con i carichi di lavoro seguenti:
- **Sviluppo di applicazioni desktop con C++**
- **Sviluppo per desktop .NET** oppure **Sviluppo multipiattaforma .NET Core**, a seconda di quale tipo di app si vuole creare.

Se Visual Studio non è installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  per installarlo gratuitamente.

Se Visual Studio è installato ma non si hanno i carichi di lavoro necessari, selezionare **Apri il Programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Nel programma di installazione di Visual Studio, selezionare i carichi di lavoro necessari e quindi **Modifica**.

## <a name="create-a-simple-native-dll"></a>Creare una semplice DLL nativa

**Per creare i file per il progetto DLL:**

1. In Visual Studio selezionare **File** > **Nuovo** > **Progetto**.

1. Nella finestra di dialogo **Nuovo progetto** in **Visual C++** selezionare **Altro** e **Progetto vuoto** nel riquadro centrale.

1. Nel campo **Nome** digitare **Mixed_Mode_Debugging** e selezionare **OK**.

   Visual Studio crea il progetto vuoto e lo visualizza in **Esplora soluzioni**.

1. In **Esplora soluzioni** selezionare **File di origine** e in seguito **Progetto** > **Aggiungi nuovo elemento**. In alternativa, fare clic con il pulsante destro del mouse su **File di origine** e selezionare **Aggiungi** > **Nuovo elemento**. 

1. Nella finestra di dialogo **Nuovo elemento** selezionare **File di C++ (.cpp)**. Digitare **Mixed_Mode.cpp** nel campo **Nome** e quindi selezionare **Aggiungi**.

    Visual Studio aggiunge il nuovo file di C++ in **Esplora soluzioni**.

1. Copiare il codice seguente nel file *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. In **Esplora soluzioni** selezionare **File di intestazione** e quindi **Progetto** > **Aggiungi nuovo elemento**. In alternativa, fare clic con il pulsante destro del mouse su **File di intestazione** e selezionare **Aggiungi** > **Nuovo elemento**. 

1. Nella finestra di dialogo **Nuovo elemento** selezionare **File di intestazione (.h)**. Digitare **Mixed_Mode.h** nel campo **Nome** e quindi selezionare **Aggiungi**.

   Visual Studio aggiunge il nuovo file di intestazione in **Esplora soluzioni**.

1. Copiare il codice seguente nel file *Mixed_Mode.h*:

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

1. Selezionare **File** > **Salva tutto** oppure premere **CTRL**+**MAIUSC**+**S** per salvare i file.

**Per configurare e compilare il progetto DLL:**

1. Sulla barra degli strumenti di Visual Studio selezionare la configurazione **Debug** e la piattaforma **x86** oppure **x64**. Se l'app chiamante è .NET Core, che viene sempre eseguita in modalità a 64 bit, selezionare la piattaforma **x64**.

1. In **Esplora soluzioni** selezionare il nodo del progetto **Mixed_Mode_Debugging** e quindi l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

1. Nella parte superiore del riquadro **Proprietà** assicurarsi che il valore di **Configurazione** sia impostato su **Attiva (debug)** e che la **Piattaforma** sia la stessa impostata sulla barra degli strumenti: **x64** o **Win32** per la piattaforma x86. 

   > [!IMPORTANT]
   > Se si passa dalla piattaforma **x86** alla **x64** o viceversa, è necessario riconfigurare le proprietà per la nuova piattaforma. 

1. In **Proprietà di configurazione** nel riquadro a sinistra selezionare **Linker** > **Avanzate** e nell'elenco a discesa accanto a **Nessun punto di ingresso** selezionare **No**. Se è necessario apportare una modifica per impostare il campo su **No**, selezionare **Applica**.

1. In **Proprietà di configurazione** selezionare **Generale** e nell'elenco a discesa accanto a **Tipo di configurazione** selezionare **Libreria dinamica (.dll)**. Selezionare **Applica** e quindi **OK**.

   ![Passare a una DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Selezionare il progetto in **Esplora soluzioni** e quindi selezionare **Compila** > **Compila soluzione**, premere **F7** o fare clic con il pulsante destro del mouse sul progetto e selezionare **Compila**.

   Il progetto dovrebbe essere compilato senza errori.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Creare una semplice app gestita per chiamare la DLL

1. In Visual Studio scegliere **File** > **Nuovo** > **Progetto**.

   > [!NOTE]
   > Anche se è possibile aggiungere il nuovo progetto gestito alla soluzione C++ esistente, la creazione di una nuova soluzione supporta più scenari di debug.

1. Nella finestra di dialogo **Nuovo progetto** selezionare **Visual C#** e nel riquadro centrale:

   - Per un'app .NET Framework, selezionare **App console (.NET Framework)**.
   
   - Per un'app .NET Core, selezionare **App console (.NET Core)**.

1. Nel campo **Nome** digitare **Mixed_Mode_Calling_App** e selezionare **OK**.

   Visual Studio crea il progetto vuoto e lo visualizza in **Esplora soluzioni**.

1. Sostituire tutto il codice in *Program.cs* con il codice seguente:

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
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
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

1. Nel nuovo codice sostituire il percorso del file in `[DllImport]` con il percorso per la DLL *Mixed_Mode_Debugging.dll* appena creata. Vedere il commento del codice per i suggerimenti. Assicurarsi di sostituire il segnaposto *username*.

1. Selezionare **File** > **Save Program.cs** oppure premere **CTRL**+**S** per salvare il file.

## <a name="configure-mixed-mode-debugging"></a>Configurare il debug in modalità mista 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Per configurare il debug in modalità mista per un'app .NET Framework 

1. In **Esplora soluzioni** selezionare il nodo del progetto **Mixed_Mode_Calling_App** e quindi l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.

1. Selezionare **Debug** nel riquadro a sinistra, selezionare la casella di controllo **Abilita debug codice nativo** e chiudere la pagina delle proprietà per salvare le modifiche.

    ![Abilitare il debug in modalità mista](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Per configurare il debug in modalità mista per un'app .NET Core 

Nella maggior parte delle versioni di Visual Studio 2017 è necessario usare il file *launchSettings.json*, anziché le proprietà del progetto, per abilitare il debug in modalità mista per il codice nativo in un'app .NET Core. Per tenere traccia degli aggiornamenti dell'interfaccia utente per questa funzionalità, vedere questo [problema di GitHub](https://github.com/dotnet/project-system/issues/1125).

1. In **Esplora soluzioni** espandere **Proprietà** e aprire il file *launchSettings.json*. 

   >[!NOTE]
   >Per impostazione predefinita, *launchSettings.json* si trova in *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Se *launchSettings.json* non esiste, selezionare il progetto **Mixed_Mode_Calling_App** in **Esplora soluzioni** e selezionare l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**. Apportare una modifica temporanea nella scheda **Debug** e compilare il progetto. In questo modo verrà creato il file *launchSettings.json*. Annullare la modifica apportata nella scheda **Debug**.

1. Nel file *lauchSettings.json* aggiungere la riga seguente:

    ```csharp
    "nativeDebugging": true
    ```

    Il file completo sarà molto simile all'esempio seguente:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Impostare un punto di interruzione e avviare il debug

1. Nel progetto C# aprire *Program.cs*. Impostare un punto di interruzione nella riga di codice seguente facendo clic sul margine di estrema sinistra, selezionando la riga e premendo **F9**, oppure facendo clic sulla riga e selezionando **Punto di interruzione** > **Inserisci punto di interruzione**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    In corrispondenza del punto di interruzione viene visualizzato un cerchio rosso.

1. Premere **F5**, selezionare la freccia verde sulla barra degli strumenti di Visual Studio, o selezionare **Debug** > **Avvia debug** per avviare il debug.

   Il debugger si fermerà in corrispondenza del punto di interruzione impostato. Una freccia gialla indica il punto in cui il debugger è attualmente in pausa.

## <a name="step-in-and-out-of-native-code"></a>Eseguire istruzioni e uscire dal codice nativo

1. Mentre il debug è in pausa nell'app gestita, premere **F11** o selezionare **Debug** > **Esegui istruzione**.

   Si apre il file di intestazione nativo *Mixed_Mode.h* e viene visualizzata la freccia gialla nel punto in cui il debugger è in pausa.

   ![Eseguire l'istruzione del codice nativo](../debugger/media/mixed-mode-step-into-native-code.png)

1. A questo punto, è possibile impostare e raggiungere i punti di interruzione e ispezionare le variabili nel codice nativo o gestito.

   - Passare il mouse sulle variabili nel codice sorgente per visualizzare i relativi valori.

   - Esaminare le variabili e i relativi valori nelle finestre **Auto** e **Variabili locali**.

   - Durante la pausa del debugger, è anche possibile usare le finestre **Espressione di controllo** e **Stack di chiamate**.

1. Premere nuovamente **F11** per fare avanzare il debugger di una riga.

1. Premere **MAIUSC**+**F11** oppure selezionare **Debug** > **Esci da istruzione/routine** per continuare l'esecuzione e sospenderla di nuovo nell'app gestita.

1. Premere **F5** o selezionare la freccia verde per continuare il debug dell'app.

La procedura è stata completata. L'esercitazione sull'esecuzione del debug in modalità mista è stata completata.

## <a name="next-step"></a>Passaggio successivo

In questa esercitazione è stato illustrato come eseguire il debug di codice nativo da un'app gestita, abilitando il debug in modalità mista. Per una panoramica delle altre funzionalità di debug, vedere:

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
