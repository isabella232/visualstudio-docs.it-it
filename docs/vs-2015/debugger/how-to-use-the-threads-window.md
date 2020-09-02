---
title: 'Procedura: usare la finestra thread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824252"
---
# <a name="how-to-use-the-threads-window"></a>Procedura: utilizzare la finestra Thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella finestra **thread** è possibile esaminare e utilizzare i thread nell'applicazione di cui si esegue il debug.  
  
 La finestra **thread** contiene una tabella in cui ogni riga rappresenta un thread nell'applicazione. Per impostazione predefinita, nella tabella sono elencati tutti i thread dell'applicazione, ma è possibile filtrare l'elenco per visualizzare solo i thread che interessano. Ogni colonna contiene un tipo di informazioni diverso. È possibile inoltre nascondere alcune colonne. Visualizzando tutte le colonne, vengono visualizzate le informazioni seguenti da sinistra verso destra:  
  
- La colonna del contrassegno, dove è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione. Per informazioni su come contrassegnare un thread, vedere [procedura: contrassegnare e non contrassegnare i thread](../debugger/how-to-flag-and-unflag-threads.md).  
  
- La colonna del thread attivo, dove una freccia gialla indica un thread attivo. Il contorno di una freccia indica il thread nel quale l'esecuzione si è interrotta nel debugger.  
  
- Colonna **ID** , che contiene il numero di identificazione per ogni thread.  
  
- La colonna **ID gestito** , che contiene i numeri di identificazione gestiti per i thread gestiti.  
  
- La colonna **Category** , che categorizza i thread come thread dell'interfaccia utente, gestori chiamate di procedure remote o thread di lavoro. Una categoria speciale identifica il thread principale dell'applicazione.  
  
- La colonna **Name** , che identifica ogni thread in base al nome, se ne ha uno o come \<No Name> .  
  
- La colonna **location** , che indica il punto in cui il thread è in esecuzione. È possibile espandere questo percorso per visualizzare lo stack di chiamate completo per il thread.  
  
- La colonna **Priority** , che contiene la priorità o la precedenza assegnata dal sistema a ogni thread.  
  
- La colonna **affinity mask** , che è una colonna avanzata che in genere è nascosta. In questa colonna viene visualizzata la maschera di affinità del processore per ogni thread. In un sistema con più processori, la maschera di affinità determina in quali processori è possibile eseguire un thread.  
  
- La colonna di **conteggio sospesa** , che contiene il numero sospeso. Questo conteggio determina se un thread può essere eseguito. Per una spiegazione del conteggio sospeso, vedere "Blocco e sblocco dei thread" più avanti in questo argomento.  
  
- La colonna del **nome del processo** , che contiene il processo a cui appartiene ogni thread. Questa colonna può risultare utile quando si esegue il debug di più processi, ma in genere è nascosta.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Per visualizzare la finestra Thread in modalità di interruzione o di esecuzione  
  
- Scegliere **finestre**dal menu **debug** , quindi fare clic su **thread**.  
  
### <a name="to-display-or-hide-a-column"></a>Per visualizzare o nascondere una colonna  
  
- Sulla barra degli strumenti nella parte superiore della finestra **thread** fare clic su **colonne**, quindi selezionare o deselezionare il nome della colonna che si desidera visualizzare o nascondere.  
  
### <a name="to-switch-the-active-thread"></a>Per passare al thread attivo  
  
- Effettuare uno dei passaggi seguenti:  
  
  - Fare doppio clic su un thread.  

  - Fare clic con il pulsante destro del mouse su un thread e scegliere **passa al thread**.  

    La freccia gialla viene visualizzata accanto al nuovo thread attivo. Il contorno grigio di una freccia identifica il thread nel quale l'esecuzione si è interrotta nel debugger.  
  
## <a name="grouping-and-sorting-threads"></a>Raggruppamento e ordinamento dei thread  
 Quando si raggruppano i thread, nella tabella viene visualizzata un'intestazione per ogni gruppo. L'intestazione contiene una descrizione del gruppo, ad esempio "Thread di lavoro" o "Thread senza flag", e un controllo albero. I thread membro di ciascuno gruppo appaiono sotto l'intestazione del gruppo. Per nascondere i thread membro di un gruppo, è possibile usare il controllo albero per comprimere il gruppo.  
  
 Poiché il raggruppamento ha la precedenza sull'ordinamento, è possibile ad esempio raggruppare i thread per categoria, per poi ordinarli in base all'ID all'interno di ogni categoria.  
  
#### <a name="to-sort-threads"></a>Per ordinare i thread  
  
1. Sulla barra degli strumenti nella parte superiore della finestra **thread** fare clic sul pulsante nella parte superiore di qualsiasi colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
2. Per invertire l'ordine, fare nuovamente clic sullo stesso pulsante.  
  
     I thread che prima erano visualizzati all'inizio dell'elenco appariranno al fondo.  
  
#### <a name="to-group-threads"></a>Per raggruppare i thread  
  
- Nella barra degli strumenti della finestra **thread** fare clic sull'elenco **Raggruppa per** , quindi fare clic sui criteri per i quali si desidera raggruppare i thread.  
  
#### <a name="to-sort-threads-within-groups"></a>Per ordinare i thread all'interno di gruppi  
  
1. Sulla barra degli strumenti nella parte superiore della finestra **thread** fare clic sull'elenco **Raggruppa per** , quindi fare clic sui criteri per i quali si desidera raggruppare i thread.  
  
2. Nella finestra **thread** fare clic sul pulsante nella parte superiore di qualsiasi colonna.  
  
     I thread verranno ordinati in base ai valori in quella colonna.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Per espandere o comprimere tutti i gruppi  
  
- Sulla barra degli strumenti nella parte superiore della finestra **thread** fare clic su **Espandi gruppi** o **Comprimi gruppi**.  
  
## <a name="searching-for-specific-threads"></a>Ricerca di thread specifici  
 In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] è possibile cercare i thread che corrispondono a una stringa specificata. Quando si esegue la ricerca dei thread nella finestra **thread** , nella finestra vengono visualizzati tutti i thread che corrispondono alla stringa di ricerca in qualsiasi colonna. Tali informazioni includono il percorso del thread che viene visualizzato all'inizio dello stack di chiamate nella colonna **location** . Per impostazione predefinita, tuttavia, non vengono eseguite ricerche nello stack di chiamate completo.  
  
#### <a name="to-search-for-specific-threads"></a>Per cercare thread specifici  
  
- Nella barra degli strumenti nella parte superiore della finestra **Thread** passare alla casella **Cerca** e:  
  
  - Digitare una stringa di ricerca, quindi premere INVIO.  

    \- - oppure -  

  - Fare clic sull'elenco a discesa accanto alla casella **Cerca** e selezionare una stringa di ricerca da una ricerca precedente.  
  
- (Facoltativo) Per includere lo stack di chiamate completo nella ricerca, selezionare **Cerca nello stack di chiamate**.  
  
## <a name="freezing-and-thawing-threads"></a>Blocco e sblocco dei thread  
 Quando si blocca un thread, l'esecuzione dello stesso da parte del sistema non viene avviata anche se le risorse sono disponibili.  
  
 Nel codice nativo è possibile sospendere o riprendere i thread chiamando le funzioni di Windows `SuspendThread` e `ResumeThread` o le funzioni MFC [CWinThread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) e [CWinThread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Se si chiama `SuspendThread` o `ResumeThread` , si modifica il *numero sospeso*, che viene visualizzato nella finestra **thread** . Tuttavia, se si blocca o sblocca un thread nativo, il numero sospesi non viene modificato. Nel codice nativo, un thread non può essere eseguito a meno che non sia sbloccato e il numero sospesi non sia pari a zero.  
  
 Nel codice gestito, il blocco o lo sblocco di un thread comporta la modifica del numero sospesi. Nel codice gestito, un thread bloccato presenta un numero sospesi pari a 1. Nel codice nativo, un thread bloccato presenta un numero sospesi pari a 0 a meno che non sia stato sospeso tramite una chiamata a `SuspendThread`.  
  
> [!NOTE]
> Quando si esegue il debug di una chiamata da codice nativo a codice gestito, il codice gestito viene eseguito nello stesso thread fisico del codice nativo che lo ha chiamato. Sospendendo o bloccando l'esecuzione del thread di codice nativo si otterrà anche il blocco del codice gestito.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Per bloccare o sbloccare l'esecuzione di un thread  
  
- Sulla barra degli strumenti nella parte superiore della finestra **thread** fare clic su **blocca thread** o **Sblocca thread**.  
  
     Questa azione influisce solo sui thread selezionati nella finestra **Thread**.  
  
## <a name="displaying-flagged-threads"></a>Visualizzazione di thread con flag  
 È possibile contrassegnare un thread a cui si vuole prestare particolare attenzione mediante un'icona nella finestra **Thread**. Per altre informazioni, vedere [procedura: contrassegnare e non contrassegnare i thread](../debugger/how-to-flag-and-unflag-threads.md). Nella finestra Thread è possibile scegliere di visualizzare tutti i thread o solo i thread con flag.  
  
#### <a name="to-display-only-flagged-threads"></a>Per visualizzare solo i thread con flag  
  
- Scegliere il pulsante flag nell'angolo superiore sinistro della finestra **thread** .  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Visualizzazione degli stack di chiamate dei thread e passaggio da un frame all'altro  
 In un programma multithread ogni thread dispone di un proprio stack di chiamate. La finestra **Thread** consente di visualizzare in modo pratico questi stack.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Per visualizzare lo stack di chiamate di un thread  
  
- Nella colonna **percorso** fare clic sul triangolo invertito accanto al percorso del thread.  
  
     Il percorso si espanderà per visualizzare lo stack di chiamate del thread.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Per visualizzare o comprimere gli stack di chiamate di tutti i thread  
  
- Sulla barra degli strumenti nella parte superiore della finestra **thread** fare clic su **Espandi stack di chiamate** o **Comprimi stack di chiamate**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md)
