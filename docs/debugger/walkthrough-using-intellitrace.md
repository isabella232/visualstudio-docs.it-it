---
title: Visualizzare gli eventi con IntelliTrace | Microsoft Docs
description: Informazioni su come usare IntelliTrace in Visual Studio Enterprise raccogliere dati su eventi specifici, categorie di eventi e singole chiamate di funzione.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ceb486aaa1564b9ee7a60cf7994fb849cf0f8260
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074111"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Visualizzare eventi con IntelliTrace in Visual Studio Enterprise (C#, Visual Basic)

È possibile usare IntelliTrace per raccogliere informazioni su eventi o categorie di eventi specifici o su singole chiamate di funzione oltre agli eventi. I passaggi seguenti illustrano come eseguire quest'operazione.

È possibile usare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Configurare IntelliTrace

È possibile provare a eseguire il debug con soli eventi IntelliTrace. Gli eventi IntelliTrace sono eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema. È possibile attivare o disattivare eventi specifici per il controllo degli eventi che IntelliTrace registra prima di avviare il debug. Per altre informazioni, vedere [Funzionalità intelliTrace.](../debugger/intellitrace-features.md)

- Attivare l'evento di IntelliTrace per l'accesso ai file. Andare alla pagina **Strumenti > Opzioni > IntelliTrace > Eventi di IntelliTrace** ed espandere la categoria **File**. Selezionare la categoria di eventi **File** . Saranno selezionati tutti gli eventi relativi ai file (accesso,  chiusura, eliminazione).

## <a name="create-your-app"></a>Creare l'app

1. Creare un'applicazione console C#. Aprire il file Program.cs e aggiungere l’istruzione `using` seguente:

    ```csharp
    using System.IO;
    ```

2. Creare un <xref:System.IO.FileStream> nel metodo Main, leggere da esso, chiuderlo ed eliminare il file. Aggiungere un'altra riga per disporre di un posto per impostare un punto di interruzione:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Impostare un punto di interruzione su `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Avviare il debug e visualizzare gli eventi IntelliTrace

1. Avviare il debug con la modalità consueta. Premere **F5 o fare** clic su **Debug > Avvia debug.**

    > [!TIP]
    > Tenere aperte **le finestre** Variabili locali **e** Auto durante il debug per visualizzare e registrare i valori in tali finestre.

2. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione. Se non viene visualizzata la finestra **Strumenti di diagnostica**, fare clic su **Debug > Finestre > Eventi di IntelliTrace**.

    Nella finestra **Strumenti di diagnostica** trovare la scheda **Eventi** (sono presenti 3 schede: **Eventi**, **Utilizzo della memoria** e **Utilizzo della CPU**). La scheda **Eventi** visualizza un elenco cronologico di eventi, fino all'ultimo evento prima dell'interruzione dell'esecuzione del debugger. Verrà visualizzato un evento denominato **Access WordSearchInputs.txt**.

    La screenshot che segue è presa da Visual Studio 2015 Update 1.

    ![Screenshot della finestra Visual Studio codice. L'esecuzione viene arrestata in corrispondenza di un punto di interruzione e nella scheda Eventi della finestra Strumenti di diagnostica vengono elencati gli eventi.](../debugger/media/intellitrace-update1.png)

3. Selezionare l'evento per espandere i dettagli.

    La screenshot che segue è presa da Visual Studio 2015 Update 1.

    ![Screenshot della scheda Eventi nella finestra Visual Studio Strumenti di diagnostica eventi. Un evento viene selezionato ed espanso per visualizzare i relativi dettagli.](../debugger/media/intellitraceupdate1-singleevent.png)

    È possibile scegliere il collegamento al percorso per aprire il file. Se il nome del percorso completo non è disponibile, viene visualizzata la finestra di dialogo **Apri file** .

    Fare **clic su** Attiva debug cronologico , che imposta il contesto del debugger sull'ora in cui è stato raccolto l'evento selezionato, visualizzando i dati cronologici in **Stack** di chiamate **,** Variabili locali e nelle altre finestre del debugger partecipanti. Se il codice sorgente è disponibile, Visual Studio sposta il puntatore sul codice corrispondente nella finestra di origine per consentirne l'analisi.

    La screenshot che segue è presa da Visual Studio 2015 Update 1.

    ![Screenshot della finestra Visual Studio codice. L'esecuzione viene arrestata in corrispondenza di un punto di interruzione, viene selezionato un evento e viene evidenziata la riga di codice corrispondente.](../debugger/media/historicaldebugging-update1.png)

4. Se il bug non viene trovato, provare ad analizzare altri eventi. È anche possibile che IntelliTrace registri le informazioni sulle chiamate in modo da eseguire le chiamate alle funzioni.

## <a name="next-steps"></a>Passaggi successivi

È possibile usare alcune delle funzionalità avanzate di IntelliTrace con il debug cronologico:

- Per visualizzare gli snapshot, vedere [Esaminare gli stati delle app precedenti usando IntelliTrace](../debugger/view-historical-application-state.md)
- Per informazioni su come esaminare le variabili ed esplorare il codice, vedere [Esaminare l'app con il debug cronologico](../debugger/historical-debugging-inspect-app.md)
