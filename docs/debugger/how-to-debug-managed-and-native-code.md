---
title: 'Esercitazione: Eseguire il Debug di codice gestito e nativo (modalità mista)'
description: Informazioni su come eseguire il debug di una DLL nativa da un'app .NET Core o .NET Framework con debug in modalità mista
ms.custom: ''
ms.date: 11/02/2018
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
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295761"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Esercitazione: Eseguire il Debug di codice gestito e nativo nella stessa sessione di debug

Visual Studio consente di abilitare più di un tipo di debugger in una sessione di debug, che viene chiamata il debug in modalità mista. In questa esercitazione descrive come eseguire il debug di codice nativo e gestito in una singola sessione di debug. 

Questa esercitazione illustra come eseguire il debug di codice nativo da un'app gestita, ma è anche possibile [eseguire il debug di codice gestito da un'app nativa](../debugger/how-to-debug-in-mixed-mode.md). Il debugger supporta anche altri tipi di debug in modalità mista, ad esempio il debug [Python e codice nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)e usando il debugger di script nei tipi di app, ad esempio ASP.NET.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Creare una semplice DLL native
> * Creare una semplice app .NET Core o .NET Framework per chiamare la DLL
> * Configurare il debug in modalità mista
> * Avviare il debugger
> * Raggiungere un punto di interruzione nell'app gestita
> * Eseguire il codice nativo

## <a name="prerequisites"></a>Prerequisiti

È necessario disporre di Visual Studio è installato, con carichi di lavoro seguenti:
- **Sviluppo di applicazioni desktop con C++**
- Entrambi **sviluppo di applicazioni desktop .NET** oppure **.NET Core lo sviluppo multipiattaforma**, a seconda di quale tipo di app a cui si desidera creare.

Se non hai Visual Studio, passare al [download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pagina per installarlo gratuitamente.

Se si è installato Visual Studio, ma non dispone di carichi di lavoro è necessario, selezionare **aperto Visual Studio Installer** nel riquadro sinistro di Visual Studio **nuovo progetto** nella finestra di dialogo. Nel programma di installazione Visual Studio, selezionare i carichi di lavoro è necessario e quindi selezionare **Modify**.

## <a name="create-a-simple-native-dll"></a>Creare una semplice DLL native

**Per creare i file per il progetto DLL:**

1. In Visual Studio, selezionare **File** > **New** > **progetto**.

1. Nel **nuovo progetto** nella finestra di dialogo **Visual C++**, selezionare **altri**, quindi selezionare **progetto vuoto** nel riquadro centrale.

1. Nel **Name** digitare **Mixed_Mode_Debugging**, quindi selezionare **OK**.

   Visual Studio crea il progetto vuoto e lo visualizza nel **Esplora soluzioni**.

1. Nelle **Esplora soluzioni**, selezionare **i file di origine**, quindi selezionare **progetto** > **Aggiungi nuovo elemento**. In alternativa, fare doppio clic su **file di origine** e selezionare **Add** > **nuovo elemento**. 

1. Nel **nuovo elemento** finestra di dialogo, seleziona **file di C++ (. cpp)**. Tipo di **Mixed_Mode.cpp** nel **Name** campo e quindi selezionare **Add**.

    Visual Studio aggiunge il nuovo file C++ **Esplora soluzioni**.

1. Copiare il codice seguente nel *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. Nelle **Esplora soluzioni**, selezionare **i file di intestazione**, quindi selezionare **progetto** > **Aggiungi nuovo elemento**. In alternativa, fare doppio clic su **file di intestazione** e selezionare **Add** > **nuovo elemento**. 

1. Nel **nuovo elemento** finestra di dialogo, seleziona **file di intestazione (h)**. Tipo di **Mixed_Mode.h** nel **Name** campo e quindi selezionare **Add**.

   Visual Studio aggiunge il nuovo file di intestazione per **Esplora soluzioni**.

1. Copiare il codice seguente nel *Mixed_Mode.h*:

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

1. Selezionare **File** > **Salva tutto** oppure premere **Ctrl**+**MAIUSC**+**S**  per salvare i file.

**Per configurare e compilare il progetto DLL:**

1. Sulla barra degli strumenti di Visual Studio, selezionare **Debug** configuration e **x86** oppure **x64** piattaforma. Se l'app chiama sarà .NET Core, che viene sempre eseguito in modalità a 64 bit, selezionare **x64** come piattaforma.

1. Nelle **Esplora soluzioni**, selezionare il **Mixed_Mode_Debugging** nodo del progetto e selezionare il **proprietà** icona, o il nodo del progetto e scegliere **Proprietà**.

1. All'inizio del **proprietà** riquadro, assicurarsi che il **Configuration** è impostata su **Active (debug)** e il **piattaforma** equivale a quello che sai impostare sulla barra degli strumenti: **x64**, o **Win32** x86 a piattaforme. 

   > [!IMPORTANT]
   > Se si passa dalla piattaforma **x86** al **x64** o viceversa, è necessario riconfigurare le proprietà per la nuova piattaforma. 

1. Sotto **le proprietà di configurazione** nel riquadro sinistro, selezionare **Linker** > **avanzate**e nell'elenco a discesa accanto a **Nessun punto di ingresso**, selezionare **No**. Se è necessario modificarlo in base ai **No**, selezionare **applica**.

1. Sotto **le proprietà di configurazione**, selezionare **generali**e nell'elenco a discesa accanto a **tipo di configurazione**, selezionare **libreria dinamica (. dll)**. Selezionare **Apply**, quindi selezionare **OK**.

   ![Passare a una DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Selezionare il progetto in **Esplora soluzioni** e quindi selezionare **compilare** > **Compila soluzione**, premere **F7**, o fare doppio clic su il progetto e selezionare **compilazione**.

   Il progetto dovrebbe essere compilato senza errori.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Creare una semplice app gestite per chiamare la DLL

1. In Visual Studio, scegliere **File** > **New** > **progetto**.

   > [!NOTE]
   > Anche se è anche possibile aggiungere il nuovo progetto gestito alla soluzione C++ esistente, creando una nuova soluzione supporta più scenari di debug.

1. Nel **nuovo progetto** finestra di dialogo **Visual C#** , quindi nel riquadro centrale:

   - Per un'app .NET Framework, selezionare **App Console (.NET Framework)**.
   
   - Per un'app .NET Core, selezionare **App Console (.NET Core)**.

1. Nel **Name** digitare **Mixed_Mode_Calling_App**, quindi selezionare **OK**.

   Visual Studio crea il progetto vuoto e lo visualizza nel **Esplora soluzioni**.

1. Sostituire tutto il codice nel *Program.cs* con il codice seguente:

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

1. Nel nuovo codice, sostituire il percorso del file in `[DllImport]` con il percorso di file per il *Mixed_Mode_Debugging.dll* appena creato. Vedere il commento del codice per i suggerimenti. Assicurarsi di sostituire il *username* segnaposto.

1. Selezionare **File** > **salvare Program.cs** oppure premere **Ctrl**+**S** per salvare il file.

## <a name="configure-mixed-mode-debugging"></a>Configurare il debug in modalità mista 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Per configurare il debug in modalità mista per un'app .NET Framework 

1. Nelle **Esplora soluzioni**, selezionare il **Mixed_Mode_Calling_App** nodo del progetto e selezionare il **proprietà** icona, o il nodo del progetto e scegliere **Proprietà**.

1. Selezionare **Debug** nel riquadro sinistro, selezionare la **Abilita debug codice nativo** casella di controllo e quindi chiudere la pagina delle proprietà per salvare le modifiche.

    ![Abilitare il debug in modalità mista](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Per configurare il debug in modalità mista per un'app .NET Core 

Nella maggior parte delle versioni di Visual Studio 2017, è necessario usare il *launchsettings. JSON* file anziché le proprietà del progetto per abilitare il debug in modalità mista per il codice nativo in un'app .NET Core. Per tenere traccia degli aggiornamenti dell'interfaccia utente per questa funzionalità, vedere questo [problema di GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Nelle **Esplora soluzioni**, espandere **delle proprietà**e aprire il *launchsettings. JSON* file. 

   >[!NOTE]
   >Per impostazione predefinita *launchsettings. JSON* Novità *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Se *launchsettings. JSON* non esiste, selezionare la **Mixed_Mode_Calling_App** progetto **Esplora soluzioni** e quindi selezionare il **proprietà** sull'icona o il progetto e scegliere **proprietà**. Apportare una modifica temporanea nel **Debug** scheda e compilare il progetto. Verrà creato un *launchsettings. JSON* file. Annullare le modifiche apportate nel **Debug** scheda.

1. Nel *lauchsettings.json* , aggiungere la riga seguente:

    ```csharp
    "nativeDebugging": true
    ```

    Il file completo avrà un aspetto simile al seguente:

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

1. Nel C# progetto, aprire *Program.cs*. Impostare un punto di interruzione nella riga di codice seguente facendo clic nel margine di estrema sinistra, selezionare la riga e premendo **F9**, oppure facendo clic sulla riga e selezionando **punto di interruzione**  >  **Inserisci punto di interruzione**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Viene visualizzato un cerchio rosso sul margine sinistro in cui è impostato il punto di interruzione.

1. Premere **F5**, selezionare la freccia verde sulla barra degli strumenti di Visual Studio, o **Debug** > **Avvia debug** per avviare il debug.

   Il debugger sospende sul punto di interruzione impostato. Una freccia gialla indica in cui il debugger è attualmente sospesa.

## <a name="step-in-and-out-of-native-code"></a>Passaggio ed estrazione del codice nativo

1. Durante il debug è in pausa nell'app gestita, premere **F11**, o selezionare **Debug** > **Esegui istruzione**.

   Il *Mixed_Mode.h* viene aperto il file di intestazione nativo e viene visualizzata la freccia gialla in cui il debugger viene sospeso.

   ![L'istruzione nel codice nativo](../debugger/media/mixed-mode-step-into-native-code.png)

1. A questo punto, è possibile impostare e raggiungere punti di interruzione e ispezionare le variabili nel codice nativo o gestito.

   - Passare il mouse sulle variabili nel codice sorgente per visualizzare i relativi valori.

   - Esaminare variabile e i relativi valori nel **Auto** e **variabili locali** windows.

   - Durante la pausa del debugger, è anche possibile usare la **Watch** windows e il **Stack di chiamate** finestra.

1. Premere **F11** nuovamente per passare la riga di un debugger.

1. Premere **Shift**+**F11** oppure selezionare **Debug** > **Esci da istruzione /** continuare l'esecuzione e sospendere di nuovo nel app gestita.

1. Premere **F5** o selezionare la freccia verde per continuare il debug dell'app.

La procedura è stata completata. È stata completata l'esercitazione sul debug in modalità mista.

## <a name="next-step"></a>Passaggio successivo

In questa esercitazione è stato illustrato come eseguire il debug di codice nativo da un'app gestita, consentendo il debug in modalità mista. Per una panoramica delle altre funzionalità di debug, vedere:

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
