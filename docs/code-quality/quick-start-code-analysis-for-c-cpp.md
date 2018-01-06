---
title: 'Guida introduttiva: Analisi del codice per C/C++ | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5fe47a5e0bb2eb8c2002c8a516ef10aa81aa0e58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="quick-start-code-analysis-for-cc"></a>Guida introduttiva all'analisi del codice per C/C++
È possibile migliorare la qualità dell'applicazione eseguendo regolarmente l'analisi del codice C o C++. Ciò consente di individuare i problemi comuni, le violazioni delle buone norme di programmazione o i difetti che sono difficili da individuare tramite test. Gli avvisi dell'analisi del codice sono diversi dagli avvisi e dagli errori del compilatore perché l'analisi del codice esegue la ricerca di modelli di codice specifici che risultano validi ma che potrebbero comunque causare problemi per gli utenti che usano il codice.  
  
## <a name="in-this-topic"></a>Contenuto dell'argomento  
  
-   [Configurare i set di regole per un progetto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Eseguire l'analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analizzare e risolvere gli avvisi dell'analisi codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Eliminazione degli avvisi di analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Creazione di elementi di lavoro per il codice gli avvisi di analisi](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Ricerca e filtro dei risultati dell'analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a>Configurare i set di regole per un progetto  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il nome del progetto e quindi scegliere **proprietà**.  
  
2.  I passaggi seguenti sono facoltativi:  
  
    1.  Nel **configurazione** e **piattaforma** gli elenchi, scegliere la piattaforma di destinazione e configurazione di compilazione.  
  
    2.  Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi del codice generato, deselezionare il **Elimina i risultati dal codice generato** casella di controllo.  
  
        > [!NOTE]
        >  Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
3.  Per eseguire l'analisi codice ogni volta che il progetto viene compilato con la configurazione selezionata, selezionare il **Attiva analisi codice per C/C++ in fase di compilazione** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice aprendo il **Analizza** menu e scegliendo **Esegui analisi del codice su** *ProjectName*.  
  
4.  Nel **eseguire il set di regole** elenco, effettuare una delle operazioni seguenti:  
  
    -   Scegliere il set di regole che si desidera usare.  
  
    -   Scegliere  **\<Sfoglia... >** per specificare set di una regola personalizzata esistente non è presente nell'elenco.  
  
    -   Definire un set di regole personalizzato.  
  
         Per ulteriori informazioni, vedere [la creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Set di regole standard C/C++  
 Visual Studio include due set standard di regole per il codice nativo:  
  
|Set di regole|Descrizione|  
|--------------|-----------------|  
|Regole minime native Microsoft|Questo set di regole è incentrato sui problemi più critici del codice nativo, inclusi i potenziali problemi di sicurezza e gli arresti anomali delle applicazioni. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.|  
|Regole consigliate native Microsoft|Questo set di regole copre un'ampia gamma di problemi. Include tutte le regole in Regole minime native Microsoft.|  
  
##  <a name="BKMK_Run"></a>Eseguire l'analisi del codice  
 Nella pagina di analisi del codice delle pagine delle proprietà del progetto è possibile configurare l'analisi del codice per eseguirla ogni volta che si compila il progetto. È inoltre possibile eseguire manualmente l'analisi del codice.  
  
 Per eseguire l'analisi del codice su una soluzione:  
  
-   Dal menu **Genera** scegliere **Esegui analisi del codice sulla soluzione**.  
  
 Per eseguire l'analisi del codice su un progetto:  
  
-   In Esplora soluzioni scegliere il nome del progetto.  
  
-   Nel **compilare** menu, scegliere **Esegui analisi del codice su** *nome progetto*.  
  
 Il progetto o la soluzione vengono compilati e viene eseguita l'analisi del codice. I risultati vengono visualizzati nella finestra Analisi codice.  
  
##  <a name="BKMK_Analyze"></a>Analizzare e risolvere gli avvisi dell'analisi codice  
 Per analizzare un avviso specifico, scegliere il titolo dell'avviso nella finestra Analisi codice. L'avviso si espande per visualizzare informazioni aggiuntive sul problema. Se possibile, l'analisi del codice consente di visualizzare i numeri di riga e la logica di analisi che ha portato all'avviso. Per informazioni dettagliate sull'avviso, incluse le possibili soluzioni al problema, scegliere l'ID dell'avviso per visualizzare l'argomento della Guida in MSDN Library per il messaggio.  
  
 Quando si espande un avviso, la riga di codice che ha provocato l'avviso viene evidenziata nell'editor del codice di Visual Studio.  
  
 Dopo aver compreso il problema, è possibile risolverlo nel codice. Eseguire quindi di nuovo l'analisi del codice per verificare che l'avviso non venga più visualizzato nella finestra Analisi codice e che la correzione non generi nuovi avvisi.  
  
> [!TIP]
>  Puoi rieseguire l'analisi del codice dalla finestra Analisi codice. Scegliere il **Analizza** pulsante e scegliere l'ambito dell'analisi. Puoi rieseguire l'analisi dell'intera soluzione o di un progetto selezionato.  
  
##  <a name="BKMK_Suppress"></a> Eliminazione degli avvisi di analisi del codice  
 In alcuni casi potresti decidere di non correggere un avviso di analisi del codice. Puoi decidere che risolvere il problema richiede un'eccessiva ricodificazione relativamente alla probabilità che il problema si ripresenti in qualsiasi implementazione realistica del codice. Oppure potresti ritenere che l'analisi utilizzata nell'avviso sia inadeguata per il contesto specifico. Puoi eliminare gli avvisi in modo che non vengano più visualizzati nella finestra Analisi codice.  
  
 Per eliminare un avviso:  
  
1.  Se le informazioni dettagliate non sono visualizzate, scegliere il titolo dell'avviso per espanderlo.  
  
2.  Scegliere il collegamento **Azioni** nella parte inferiore dell'avviso.  
  
3.  Scegliere **Elimina messaggio** e quindi scegliere **In origine**.  
  
 L'eliminazione di un messaggio inserisce un `#pragma warning (disable:`*WarningId*`)` che elimina l'avviso per la riga di codice.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Creazione di elementi di lavoro per il codice gli avvisi di analisi  
 È possibile usare la funzionalità di gestione degli elementi di lavoro per registrare bug da Visual Studio. Per usare questa funzionalità, collegarsi a un'istanza di Team Foundation Server.  
  
 **Per creare un elemento di lavoro per uno o più avvisi del codice C/C++**  
  
1.  Nella finestra Analisi codice espandere e selezionare l'avviso.  
  
2.  Nel menu di scelta rapida per gli avvisi scegliere **Crea elemento di lavoro**, quindi scegliere il tipo di elemento di lavoro.  
  
3.  Visual Studio crea un singolo elemento di lavoro per gli avvisi selezionati e visualizza l'elemento di lavoro in una finestra del documento dell'IDE.  
  
4.  Aggiungere eventuali informazioni aggiuntive e quindi scegliere **Salva elemento di lavoro**.  
  
##  <a name="BKMK_Search"></a> Ricerca e filtro dei risultati dell'analisi del codice  
 Puoi effettuare una ricerca in lunghi elenchi di messaggi di avviso e filtrare gli avvisi nelle soluzioni composte da più progetti.  
  
1.  **Per filtrare gli avvisi per titolo o id avviso**: immettere la parola chiave nel **filtro** casella di testo.  
  
2.  **Per filtrare gli avvisi per progetto**: In una soluzione multiprogetto, scegliere uno o più progetti nell'elenco nella parte superiore destra della finestra Analisi codice. Scegliere il nome della soluzione per visualizzare tutti gli avvisi.  
  
3.  **Per filtrare gli avvisi per gravità**: per impostazione predefinita, ai messaggi di analisi codice viene assegnato un livello di gravità **avviso**. È possibile assegnare la gravità di una o più messaggi come **errore** impostato in una regola personalizzata. Scegliere **avviso** o **errore** per visualizzare solo i messaggi che vengono assegnati il rispettivo livello di gravità. Scegliere **tutti** per visualizzare tutti i messaggi.