---
title: Utilizzo CPU | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af6d58ac5cd87523124d567e36559a82d69ddfc6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810533"
---
# <a name="cpu-usage"></a>Utilizzo CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando è necessario analizzare i problemi relativi alle prestazioni dell'app, è consigliabile partire dall'analisi dell'utilizzo della CPU. Lo strumento **Utilizzo CPU** indica i punti in cui la CPU impiega più tempo per l'esecuzione di codice di Visual C++, Visual C#/Visual Basic e JavaScript.  
  
 A partire da Visual Studio 2015 Update 1, è possibile visualizzare i dettagli dell'utilizzo della CPU a livello di singole funzioni senza uscire dal debugger. È possibile attivare o disattivare la profilatura della CPU durante il debug e visualizzare i risultati quando l'esecuzione viene interrotta, ad esempio in corrispondenza di un punto di interruzione. Per altre informazioni, vedere il blog relativo alla [profilatura della CPU nel debugger di Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/profile-your-cpu-in-the-debugger-in-visual-studio-2015.aspx).  
  
 Per una procedura dettagliata in cui vengono analizzate le prestazioni di un'app di Windows Store, vedere [Analizzare l'utilizzo della CPU nelle app dello Store](https://msdn.microsoft.com/library/windows/apps/dn641982.aspx).  
  
 L'hub Prestazioni e diagnostica include numerose altre opzioni per eseguire e gestire la sessione di diagnostica. È ad esempio possibile eseguire lo strumento **Utilizzo CPU** in computer locali o remoti oppure in un simulatore o in un emulatore. È possibile analizzare le prestazioni di un progetto aperto in Visual Studio o collegato a un'app in esecuzione oppure avviare un'app installata da Windows Store. Per altre informazioni, vedere [eseguire strumenti di profilatura senza il debug](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Raccogliere i dati di utilizzo della CPU  
  
1. In Visual Studio impostare la configurazione della soluzione su **Versione** e scegliere la destinazione di distribuzione.  
  
    ![Selezionare versione e computer locale](../profiling/media/cpuuse-selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
   -   Eseguendo l'app in modalità **Versione** si otterrà una migliore visualizzazione delle effettive prestazioni dell'app.  
  
   -   L'esecuzione dell'app nel computer locale consente di replicare al meglio l'esecuzione dell'app installata.  
  
   -   Se si intende raccogliere dati da un dispositivo remoto, eseguire l'app direttamente nel dispositivo e non tramite Connessione Desktop remoto.  
  
   -   Per le app di Windows Phone la raccolta dei dati direttamente dal **Dispositivo** consente di ottenere i dati più accurati.  
  
2. Scegliere **Profiler prestazioni** dal menu **Debug**.  
  
3. Scegliere **Utilizzo CPU** e quindi **Avvio**.  
  
    ![Scegliere Utilizzo CPU](../profiling/media/cpuuse-lib-choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4. All'avvio dell'app fare clic su **Get Max Number**. Attendere circa un secondo dopo la visualizzazione dell'app, quindi scegliere **Get Max Number Async**. L'attesa tra i clic sui pulsanti consente di isolare in modo più semplice le routine relative ai clic nel report di diagnostica.  
  
5. Dopo la visualizzazione della seconda riga di output, scegli **Arresta raccolta** nell'hub Prestazioni e diagnostica.  
  
   ![Arrestare la raccolta di dati di CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Lo strumento Utilizzo CPU analizza i dati e visualizza il report.  
  
   ![Report di CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analizzare il report di Utilizzo CPU  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Albero delle chiamate di Utilizzo CPU  
 Per iniziare a comprendere le informazioni dell'albero delle chiamate, selezionare di nuovo il segmento `GetMaxNumberButton_Click` e analizzare i dettagli dell'albero.  
  
####  <a name="BKMK_Call_tree_structure"></a> Struttura dell'albero delle chiamate  
 ![GetMaxNumberButton&#95;Fare clic sull'albero delle chiamate](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Passaggio 1](../profiling/media/procguid-1.png "ProcGuid_1")|Il nodo di livello principale nell'albero delle chiamate di Utilizzo CPU è uno pseudo-nodo|  
|![Passaggio 2](../profiling/media/procguid-2.png "ProcGuid_2")|Nella maggior parte delle app, quando l'opzione **Mostra codice esterno** è disabilitata, il nodo di secondo livello è un nodo **[Codice esterno]** contenente il codice di sistema e di framework che avvia e arresta l'app, disegna l'interfaccia utente, controlla la pianificazione dei thread e fornisce altri servizi di basso livello all'app.|  
|![Passaggio 3](../profiling/media/procguid-3.png "ProcGuid_3")|Gli elementi figlio del nodo di secondo livello sono i metodi del codice utente e le routine asincrone che vengono chiamati o creati dal codice di sistema o di framework di secondo livello.|  
|![Passaggio 4](../profiling/media/procguid-4.png "ProcGuid_4")|I nodi figlio di un metodo contengono i dati solo per le chiamate del metodo padre. Quando l'opzione **Mostra codice esterno** è disabilitata, i metodi dell'app possono contenere anche un nodo **[Codice esterno]** .|  
  
####  <a name="BKMK_External_Code"></a> Codice esterno  
 Il codice esterno rappresenta funzioni nei componenti del sistema e del framework che vengono eseguite dal codice scritto. Include funzioni che avviano e arrestano l'app, disegnano l'interfaccia utente, controllano il threading e forniscono altri servizi di basso livello all'app. Nella maggior parte dei casi il codice esterno è poco interessante, per questo motivo l'albero delle chiamate di Utilizzo CPU raccoglie le funzioni esterne di un metodo utente in un unico nodo **[Codice esterno]** .  
  
 Se vuoi visualizzare i percorsi delle chiamate del codice esterno, scegli **Mostra codice esterno** nell'elenco **Visualizzazione filtro** e quindi scegli **Applica**.  
  
 ![Scegliere Visualizzazione filtro e quindi Mostra codice esterno](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Tieni presente che numerose catene di chiamate del codice esterno sono molto annidate, pertanto la larghezza della colonna Nome funzione può superare la larghezza di visualizzazione in quasi tutti i monitor, ad eccezione di quelli più grandi. Quando ciò si verifica, i nomi delle funzioni sono visualizzati come **[…]**:  
  
 ![Codice esterno annidato nell'albero delle chiamate](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Usa la casella di ricerca per trovare il nodo che stai cercando, quindi usa la barra di scorrimento orizzontale per visualizzare i dati:  
  
 ![Ricerca di codice esterno annidato](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Colonne di dati dell'albero delle chiamate  
  
|||  
|-|-|  
|**CPU totale (%)**|![Equazione dei dati % totali](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Percentuale dell'attività CPU dell'app nell'intervallo di tempo selezionato usata dalle chiamate alla funzione e dalle funzioni chiamate dalla funzione. Osservare che si tratta di un valore diverso da quello del grafico della sequenza temporale di **Utilizzo CPU** , che mette a confronto l'attività totale dell'app in un intervallo di tempo con la capacità CPU disponibile totale.|  
|**CPU auto (%)**|![Equazione auto %](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Percentuale dell'attività CPU dell'app nell'intervallo di tempo selezionato usata dalle chiamate alla funzione, esclusa l'attività delle funzioni chiamate dalla funzione.|  
|**CPU totale (ms)**|Numero di millisecondi usati nelle chiamate alla funzione nell'intervallo di tempo selezionato e per le funzioni chiamate dalla funzione.|  
|**CPU auto (ms)**|Numero di millisecondi usati nelle chiamate alla funzione nell'intervallo di tempo selezionato e per le funzioni chiamate dalla funzione.|  
|**Modulo**|Nome del modulo contenente la funzione o numero dei moduli contenenti le funzioni in un nodo [Codice esterno].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funzioni asincrone nell'albero delle chiamate di Utilizzo CPU  
 Quando il compilatore rileva un metodo asincrono, crea una classe nascosta per controllare l'esecuzione del metodo. Concettualmente, la classe è una macchina a stati che include un elenco di funzioni generate dal compilatore che chiamano le operazioni del metodo originale in modo asincrono, nonché i callback, l'utilità di pianificazione e gli iteratori necessari. Quando il metodo originale viene chiamato da un metodo padre, il runtime rimuove il metodo dal contesto di esecuzione del padre ed esegue i metodi della classe nascosta nel contesto del codice di sistema e di framework che controllano l'esecuzione dell'app. Spesso, ma non sempre, i metodi asincroni vengono eseguiti in uno o più thread diversi. Il codice è illustrato nell'albero delle chiamate di Utilizzo CPU come figlio del nodo **[Codice esterno]** immediatamente sotto il nodo principale dell'albero.  
  
 Per vedere questo aspetto nel nostro esempio, seleziona di nuovo il segmento `GetMaxNumberAsyncButton_Click` nella sequenza temporale.  
  
 ![GetMaxNumberAsyncButton&#95;Fare clic sulla selezione del report](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 I primi due nodi sotto **[Codice esterno]** sono i metodi generati dal compilatore della classe macchina a stati. Il terzo è la chiamata al metodo originale. Espandendo i metodi generati puoi vedere ciò che succede.  
  
 ![Expanded GetMaxNumberAsyncButton&#95;Fare clic sull'albero](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` fa molto poco: gestisce un elenco dei valori delle attività, calcola il massimo dei risultati e mostra l'output.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` mostra l'attività necessaria per pianificare e avviare le 48 attività che eseguono il wrapping della chiamata a `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` mostra le operazioni eseguite dalle attività che chiamano `GetNumber`.



