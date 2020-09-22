---
title: 'Procedura dettagliata: utilizzo di IntelliTrace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d18ae0684dab5b6dc5c4001b93804bb13aa75e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839607"
---
# <a name="walkthrough-using-intellitrace"></a>Procedura dettagliata: Utilizzo di IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare IntelliTrace per raccogliere informazioni su eventi o categorie di eventi specifici o su singole chiamate di funzione oltre agli eventi. I passaggi seguenti illustrano come eseguire quest'operazione.  
  
 È possibile utilizzare IntelliTrace in Visual Studio Enterprise edition (ma non le edizioni Professional o Community).  
  
## <a name="using-intellitrace-with-events-only"></a><a name="GettingStarted"></a> Uso di IntelliTrace con solo eventi  
 È possibile provare a eseguire il debug con soli eventi IntelliTrace. Gli eventi IntelliTrace sono eventi del debugger, eccezioni, eventi .NET Framework e altri eventi di sistema. È possibile attivare o disattivare eventi specifici per il controllo degli eventi che IntelliTrace registra prima di avviare il debug. Per ulteriori informazioni, vedere [funzionalità di IntelliTrace](../debugger/intellitrace-features.md).  
  
 La procedura seguente illustra come eseguire il debug con soli eventi IntelliTrace:  
  
1. Attivare l'evento di IntelliTrace per l'accesso ai file. Andare alla pagina **Strumenti/Opzioni/IntelliTrace/eventi IntelliTrace** ed espandere la categoria **file** . Selezionare la categoria di eventi **File** . Saranno selezionati tutti gli eventi relativi ai file (accesso,  chiusura, eliminazione).  
  
2. Creare un'applicazione console C#. Aprire il file Program.cs e aggiungere l’istruzione `using` seguente:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3. Creare un <xref:System.IO.FileStream> nel metodo Main, leggere da esso, chiuderlo ed eliminare il file. Aggiungere un'altra riga per disporre di un posto per impostare un punto di interruzione:  
  
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
  
4. Impostare un punto di interruzione su `Console.WriteLine("done");`  
  
5. Avviare il debug con la modalità consueta. (Premere **F5** o fare cli su **Debug / Avvia debug**.  
  
    > [!TIP]
    > Mantenere le finestre **Variabili locali** e **Auto** aperte durante il debug per visualizzare e registrare i valori visualizzati in queste finestre.  
  
6. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione. Se la finestra di **strumenti di diagnostica** non viene visualizzata, fare clic su **debug/Windows/eventi IntelliTrace**.  
  
     Nella finestra **Strumenti di diagnostica** trovare la scheda **Eventi** (sono presenti 3 schede: **Eventi**, **Utilizzo della memoria**e **Utilizzo della CPU**). La scheda **Eventi** visualizza un elenco cronologico di eventi, fino all'ultimo evento prima dell'interruzione dell'esecuzione del debugger. Verrà visualizzato un evento denominato **Access WordSearchInputs.txt**.  
  
     La screenshot che segue è presa da Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
7. Selezionare l'evento per espandere i dettagli.  
  
     La screenshot che segue è presa da Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     È possibile scegliere il collegamento al percorso per aprire il file. Se il nome del percorso completo non è disponibile, viene visualizzata la finestra di dialogo **Apri file** .  
  
     Fare clic su **Attivare debug cronologico**, che imposta il contesto del debugger sul momento in cui l'evento selezionato è stato raccolto, mostrando i dati cronologici nelle finestre **Stack di chiamate**, **Variabili locali** e altre finestre del debugger partecipanti. Se il codice sorgente è disponibile, Visual Studio sposta il puntatore sul codice corrispondente nella finestra di origine per consentirne l'analisi.  
  
     La screenshot che segue è presa da Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
8. Se il bug non viene trovato, provare ad analizzare altri eventi. È anche possibile che IntelliTrace registri le informazioni sulle chiamate in modo da eseguire le chiamate alle funzioni.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Utilizzo di IntelliTrace con eventi e chiamate di funzione  
 IntelliTrace consente di registrare le chiamate di funzione insieme agli eventi. In tal modo è possibile visualizzare la cronologia dello stack di chiamate e scorrere in avanti e indietro le chiamate nel codice. IntelliTrace registra i dati, ad esempio nomi delle funzioni, punti di ingresso e uscita delle funzioni e alcuni valori di parametri e valori restituiti. Vedere [funzionalità di IntelliTrace](../debugger/intellitrace-features.md).  
  
1. Attivare la raccolta delle chiamate. (In **Strumenti / Opzioni / IntelliTrace / Generale**, selezionare **Eventi IntelliTrace e informazioni di chiamata**. IntelliTrace inizierà a raccogliere tali informazioni all'avvio della sessione di debug successiva.  
  
    > [!TIP]
    > Ciò potrebbe rallentare l'applicazione e aumentare le dimensioni dei file di log di IntelliTrace (file .iTrace) salvati sul disco. Per ottenere la maggior parte dei dati delle chiamate riducendo al contempo gli effetti, registrare solo i dati da quei moduli che interessano. Per modificare la dimensione massima dei file .iTrace, passare a **Strumenti / Opzioni / IntelliTrace / Avanzate**e specificare la dimensione massima dello spazio su disco. Il valore predefinito è 250 MB.  
  
2. Avviare il debug dell'applicazione console C# creata nella sezione precedente. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione. Se la finestra di **strumenti di diagnostica** non viene visualizzata, fare clic su **debug/Windows/eventi IntelliTrace**.  
  
3. Passare alla scheda **Chiamate** .  
  
     Ora vengono visualizzate le chiamate alle funzioni dell’applicazione, a partire dalla chiamata radice (nella soluzione corrente, il punto di ingresso di Main) e terminando con la posizione in cui l'esecuzione si è interrotta.  
  
     Selezionare una delle chiamate alle funzioni e fare doppio clic. Verranno visualizzati i punti di ingresso e uscita della funzione, nonché le chiamate effettuate dalla chiamata corrente ad altre funzioni e gli eventi di IntelliTrace generati dalla chiamata. Se il debug cronologico non è attivo, viene attivato da questa azione. Per altre informazioni sul debug cronologico, vedere [Historical Debugging](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    > È possibile riscontrare che alcune chiamate sono visualizzate in grigio. Le chiamate vengono visualizzate in grigio perché IntelliTrace non ha registrato i dati dei moduli corrispondenti. Per visualizzare questi dati, impostare la raccolta dei dati da tali moduli da parte di IntelliTrace. Per informazioni sulla specifica dei moduli, vedere [funzionalità di IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Passaggi successivi
