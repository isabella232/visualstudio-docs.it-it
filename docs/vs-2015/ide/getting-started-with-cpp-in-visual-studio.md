---
title: Guida introduttiva a C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001b394d86e56b172bb1a50c335bd8ba5bcacb15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645621"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Guida introduttiva a C++ in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Completando questa procedura dettagliata è possibile acquisire familiarità con molti strumenti e finestre di dialogo utili per lo sviluppo di applicazioni con Visual Studio. Durante la procedura gli utenti potranno creare una semplice applicazione in stile "Hello, World", acquisendo al contempo altre informazioni su come lavorare in IDE (Integrated Development Environment).

 In questo argomento sono incluse le sezioni seguenti:

 [Accedi a Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Creare un'applicazione semplice](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Aggiungere codice all'applicazione](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Eseguire il debug e il test dell'applicazione](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Compilare una versione di rilascio dell'applicazione](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="sign-in-to-visual-studio"></a><a name="BKMK_Configure"></a> Accedi a Visual Studio
 La prima volta che si avvia Visual Studio, è possibile eseguire l'accesso con il proprio account Microsoft, ad esempio Live o Outlook. L'esecuzione dell'accesso consente di sincronizzare le impostazioni tra tutti i dispositivi. Per altre informazioni, vedere [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md).

 Figura 1: IDE di Visual Studio

 ![IDE con impostazioni Visual C&#43;&#43; applicate](../ide/media/c-ide-defaultenvironmentlayout.png "IDE_DefaultEnvironmentLayout c++")

 Dopo aver aperto Visual Studio, saranno visibili le tre parti fondamentali dell'IDE, vale a dire le finestre degli strumenti, i menu e le barre degli strumenti e lo spazio della finestra principale. Le finestre degli strumenti sono ancorate ai lati sinistro e destro della finestra dell'applicazione, con **Avvio veloce**, la barra dei menu e la barra degli strumenti standard nella parte superiore. Al centro della finestra dell'applicazione si trova la **Pagina iniziale**. Quando si apre una soluzione o un progetto, in questo spazio verranno visualizzati gli editor e le finestre di progettazione. Quando si sviluppa un'applicazione, la maggiore parte del tempo verrà dedicata a questa area centrale.

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> Creare un'applicazione semplice
 Quando si crea un'applicazione in Visual Studio, è necessario prima di tutto creare un progetto e una soluzione. In questo esempio viene creata un'applicazione console di Windows.

#### <a name="to-create-a-console-app"></a>Per creare un'applicazione console

1. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.

    ![Sulla barra dei menu scegliere file, nuovo, progetto](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. Nella categoria **Visual C++** scegliere il modello **Progetto console Win32** , quindi denominare il progetto `GreetingsConsoleApp`.

    ![Modello Progetto console Win32](../ide/media/c-ide-newprojectdlg.png "IDE_NewProjectDlg c++")

3. Quando viene visualizzata la Creazione guidata applicazione Win32, scegliere **Fine** .

    ![Creazione guidata applicazione console Win32](../ide/media/c-ide-win32consoleappwizard.png "IDE_Win32ConsoleAppWizard c++")

   Il progetto e la soluzione GreetingsConsoleApp, con i file di base per un progetto console Win32, verranno creati e automaticamente caricati in **Esplora soluzioni**. Il file GreetingsConsoleApp.cpp viene aperto nell'editor di codice. In **Esplora soluzioni**vengono visualizzati gli elementi indicati di seguito.

   Figura 4: Elementi di progetto

   ![File per la soluzione in Esplora soluzioni](../ide/media/c-ide-solutioncontents.png "IDE_SolutionContents c++")

## <a name="add-code-to-the-application"></a><a name="BKMK_AddCode"></a> Aggiungere codice all'applicazione
 In seguito, verrà aggiunto il codice per visualizzare la parola "Hello" nella finestra della console.

#### <a name="to-display-hello-in-the-console-window"></a>Per visualizzare "Hello" nella finestra della console

1. Nel file GreetingsConsoleApp.cpp, inserire una riga vuota prima della riga `return 0;` e quindi immettere il codice seguente:

    ```
    cout << "Hello\n";
    ```

     Una linea rossa ondulata appare sotto `cout`. Se si posiziona il mouse sulla linea, verrà visualizzato un messaggio di errore.

     ![Testo dell'errore per cout](../ide/media/c-ide-couterror.png "IDE_CoutError c++")

     Il messaggio di errore viene visualizzato anche nella finestra **Elenco errori** . È possibile visualizzare la finestra vicino o sulla barra dei menu, scegliendo **Visualizzazione**, **Elenco errori**.

     [cout](https://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) è incluso nel \<iostream\> file di intestazione.

2. Per includere l'intestazione iostream, immettere il codice seguente dopo `#include "stdafx.h"`:

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Come è possibile notare, dopo aver immesso il codice viene visualizzato un riquadro contenente suggerimenti per i caratteri immessi. Questo riquadro fa parte di IntelliSense per C++, che fornisce prompt di codifica, inclusi gli elenchi di classi o membri di interfaccia e informazioni sui parametri. È anche possibile usare frammenti di codice, cioè blocchi di codice predefiniti. Per altre informazioni, vedere [uso di IntelliSense](../ide/using-intellisense.md) e [frammenti di codice](../ide/code-snippets.md).

     La sottolineatura ondulata di colore rosso sotto `cout` scomparirà dopo aver risolto l'errore.

3. Salvare le modifiche apportate al file.

     ![Codice che risolve l'errore cout](../ide/media/c-ide-coutfix.png "IDE_CoutFix c++")

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> Eseguire il debug e il test dell'applicazione
 È possibile eseguire il debug del file GreetingsConsoleApp per verificare se la parola "Hello" viene visualizzata nella finestra della console.

#### <a name="to-debug-the-application"></a>Per eseguire il debug dell'applicazione

- Avviare il debugger.

     ![Comando Avvia Debug dal menu Debug](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

     Il debugger viene avviato e viene eseguito il codice. La finestra della console (una finestra separata simile a un prompt dei comandi) viene visualizzata per pochi secondi, ma si chiude rapidamente quando il debugger si arresta. Per visualizzare il testo, è necessario impostare un punto di interruzione per arrestare l'esecuzione del programma.

#### <a name="to-add-a-breakpoint"></a>Per aggiungere un punto di interruzione

1. Aggiungere un punto di interruzione dalla barra dei menu in corrispondenza della riga `return 0;`. È anche possibile fare clic sul margine sinistro per impostare un punto di interruzione.

    ![Comando Imposta/Rimuovi punto di interruzione nel menu Debug](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint (")

    Accanto alla riga di codice nel margine di estrema sinistra della finestra dell'editor verrà visualizzato un cerchio rosso.

2. Premere il tasto F5 per avviare il debug.

    Il debugger viene avviato, e viene visualizzata una finestra della console con la parola **Hello**.

    ![Testo Hello nella finestra del prompt dei comandi di Windows](../ide/media/c-ide-hellocommandwindow.png "IDE_HelloCommandWindow c++")

3. Premere MAIUSC+F5 per arrestare il debug.

   Per altre informazioni, vedere [Console Projects](../debugger/debugging-preparation-console-projects.md) (Progetti console).

## <a name="build-a-release-version-of-the-app"></a><a name="BKMK_BuildRelease"></a> Compilare una versione di rilascio dell'app
 Dopo aver verificato che tutto funzioni, sarà possibile preparare una compilazione di rilascio dell'applicazione.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Per pulire i file della soluzione e compilare una versione di rilascio

1. Dalla barra dei menu, eliminare i file intermedi e i file di output creati durante le compilazioni precedenti.

    ![Comando Pulisci soluzione del menu Compila](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Modificare la configurazione di compilazione per GreetingsConsoleApp da **Debug** a **Rilascio**.

    ![Compilare una versione di rilascio dell'applicazione](../ide/media/c-ide-changingbuildtorelease.png "IDE_ChangingBuildtoRelease c++")

3. Compilare la soluzione.

    ![Comando Compila soluzione del menu Compila](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   La procedura dettagliata è stata completata. Per esaminare altri esempi, vedere [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: Creare un'applicazione semplice](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [Suggerimenti per la produttività](../ide/productivity-tips-for-visual-studio.md) [Esempi di Visual Studio](../ide/visual-studio-samples.md) [Introduzione allo sviluppo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)
