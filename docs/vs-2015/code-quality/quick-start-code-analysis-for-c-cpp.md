---
title: 'Avvio rapido: analisi del codice per CC++ -| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278476"
---
# <a name="quick-start-code-analysis-for-cc"></a>Guida introduttiva all'analisi del codice per C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile migliorare la qualità dell'applicazione eseguendo regolarmente l'analisi del codice C o C++. Ciò consente di individuare i problemi comuni, le violazioni delle buone norme di programmazione o i difetti che sono difficili da individuare tramite test. Gli avvisi di analisi del codice sono diversi rispetto agli errori e agli avvisi del compilatore in quanto durante l'analisi del codice vengono cercati modelli di codice specifici che risultano validi ma che potrebbero causare problemi a te o ad altre persone che usano il codice.  
  
## <a name="in-this-topic"></a>In questo argomento  
  
- [Configurare i set di regole per un progetto](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Esegui analisi codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analizzare e risolvere gli avvisi di analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Eliminazione degli avvisi di analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Creazione di elementi di lavoro per gli avvisi di analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Ricerca e filtro dei risultati dell'analisi del codice](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="BKMK_ConfigureRuleSets"></a>Configurare i set di regole per un progetto  
  
1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nome del progetto, quindi scegliere **Proprietà**.  
  
2. I passaggi seguenti sono facoltativi:  
  
    1. Negli elenchi **configurazione** e **piattaforma** scegliere la configurazione di compilazione e la piattaforma di destinazione.  
  
    2. Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi dal codice generato, deselezionare la casella di controllo non **visualizzare i risultati del codice generato** .  
  
        > [!NOTE]
        > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.  
  
3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato usando la configurazione selezionata, selezionare la casella di controllo **Abilita analisi codice per la compilazione C/C++ on** . È anche possibile eseguire manualmente l'analisi del codice aprendo il menu **analizza** e quindi scegliendo **Esegui analisi codice su** *NomeProgetto*.  
  
4. Nell'elenco **Esegui questo set di regole** effettuare una delle operazioni seguenti:  
  
    - Scegliere il set di regole che si desidera usare.  
  
    - Scegliere **\<Sfoglia... >** per specificare un set di regole personalizzato esistente non presente nell'elenco.  
  
    - Definire un set di regole personalizzato.  
  
         Per altre informazioni, vedere [creazione di set di regole personalizzati](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Set di regole standard C/C++  
 Visual Studio include due set standard di regole per il codice nativo:  
  
|Set di regole|Descrizione|  
|--------------|-----------------|  
|Regole minime native Microsoft|Questo set di regole è incentrato sui problemi più critici del codice nativo, inclusi i potenziali problemi di sicurezza e gli arresti anomali delle applicazioni. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.|  
|Regole consigliate native Microsoft|Questo set di regole copre un'ampia gamma di problemi. Include tutte le regole in Regole minime native Microsoft.|  
  
## <a name="BKMK_Run"></a>Esegui analisi codice  
 Nella pagina di analisi del codice delle pagine delle proprietà del progetto è possibile configurare l'analisi del codice per eseguirla ogni volta che si compila il progetto. È inoltre possibile eseguire manualmente l'analisi del codice.  
  
 Per eseguire l'analisi del codice su una soluzione:  
  
- Dal menu **Genera** scegliere **Esegui analisi del codice sulla soluzione**.  
  
  Per eseguire l'analisi del codice su un progetto:  
  
- In Esplora soluzioni scegliere il nome del progetto.  
  
- Nel menu **Compila** scegliere **Esegui analisi codice sul nome del** *progetto*.  
  
  Il progetto o la soluzione vengono compilati e viene eseguita l'analisi del codice. I risultati vengono visualizzati nella finestra Analisi codice.  
  
## <a name="BKMK_Analyze"></a>Analizzare e risolvere gli avvisi di analisi del codice  
 Per analizzare un avviso specifico, scegliere il titolo dell'avviso nella finestra Analisi codice. L'avviso si espande per visualizzare informazioni aggiuntive sul problema. Se possibile, l'analisi del codice consente di visualizzare i numeri di riga e la logica di analisi che ha portato all'avviso. Per informazioni dettagliate sull'avviso, incluse le possibili soluzioni al problema, scegliere l'ID dell'avviso per visualizzare l'argomento della Guida in MSDN Library per il messaggio.  
  
 Quando espandi un avviso, la riga di codice che ha provocato l'avviso viene evidenziata nell'editor di codice di Visual Studio.  
  
 Dopo aver compreso il problema, è possibile risolverlo nel codice. Riesegui quindi l'analisi del codice per verificare che l'avviso non venga più visualizzato nella finestra Analisi codice e che la correzione non generi nuovi avvisi.  
  
> [!TIP]
> Puoi rieseguire l'analisi del codice dalla finestra Analisi codice. Scegliere il pulsante **analizza** e scegliere l'ambito dell'analisi. Puoi rieseguire l'analisi dell'intera soluzione o di un progetto selezionato.  
  
## <a name="BKMK_Suppress"></a> Eliminazione degli avvisi di analisi del codice  
 In alcuni casi potresti decidere di non correggere un avviso di analisi del codice. Puoi decidere che risolvere il problema richiede un'eccessiva ricodificazione relativamente alla probabilità che il problema si ripresenti in qualsiasi implementazione realistica del codice. Oppure potresti ritenere che l'analisi utilizzata nell'avviso sia inadeguata per il contesto specifico. Puoi eliminare gli avvisi in modo che non vengano più visualizzati nella finestra Analisi codice.  
  
 Per eliminare un avviso:  
  
1. Se le informazioni dettagliate non sono visualizzate, scegliere il titolo dell'avviso per espanderlo.  
  
2. Scegliere il collegamento **Azioni** nella parte inferiore dell'avviso.  
  
3. Scegliere non **visualizzare il messaggio** , quindi scegliere **nell'origine**.  
  
   L'eliminazione di un messaggio inserisce un `#pragma warning (disable:`*WarningId*`)` che elimina l'avviso per la riga di codice.  
  
## <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Creazione di elementi di lavoro per gli avvisi di analisi del codice  
 È possibile usare la funzionalità di gestione degli elementi di lavoro per registrare bug da Visual Studio. Per usare questa funzionalità, collegarsi a un'istanza di Team Foundation Server.  
  
 **Per creare un elemento di lavoro per uno o più avvisiC++ C/code**  
  
1. Nella finestra Analisi codice espandere e selezionare l'avviso.  
  
2. Nel menu di scelta rapida per gli avvisi, scegliere **Crea elemento di lavoro**, quindi scegliere il tipo di elemento di lavoro.  
  
3. Visual Studio crea un singolo elemento di lavoro per gli avvisi selezionati e visualizza l'elemento di lavoro in una finestra del documento dell'IDE.  
  
4. Aggiungere eventuali informazioni aggiuntive, quindi scegliere **Salva elemento di lavoro**.  
  
## <a name="BKMK_Search"></a> Ricerca e filtro dei risultati dell'analisi del codice  
 Puoi effettuare una ricerca in lunghi elenchi di messaggi di avviso e filtrare gli avvisi nelle soluzioni composte da più progetti.  
  
1. **Per filtrare gli avvisi per titolo o ID avviso**: immettere la parola chiave nella casella di testo **filtro** .  
  
2. **Per filtrare gli avvisi per progetto**: in una soluzione multiprogetto, scegliere uno o più progetti nell'elenco nella parte superiore destra della finestra analisi codice. Scegliere il nome della soluzione per visualizzare tutti gli avvisi.  
  
3. **Per filtrare gli avvisi in base alla gravità**: per impostazione predefinita, ai messaggi di analisi del codice viene assegnata una gravità di **avviso**. È possibile assegnare la gravità di uno o più messaggi come **errore** in un set di regole personalizzato. Scegliere **avviso** o **errore** per visualizzare solo i messaggi a cui è assegnata la rispettiva gravità. Scegliere **tutti** per visualizzare tutti i messaggi.
