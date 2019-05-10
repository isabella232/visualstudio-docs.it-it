---
title: 'Avvio rapido: Analisi codice per C/C++'
description: Eseguire l'analisi statica sul C++ in Visual Studio per rilevare i problemi comuni di codifica e i difetti del codice.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 039ffcd1717dba8ec3c76ae1ca4a691d60851ee5
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226081"
---
# <a name="quickstart-code-analysis-for-cc"></a>Guida introduttiva: Analisi codice per C/C++

È possibile migliorare la qualità dell'applicazione eseguendo regolarmente l'analisi del codice C o C++. Ciò consente di individuare i problemi comuni, le violazioni delle buone norme di programmazione o i difetti che sono difficili da individuare tramite test. Gli avvisi di analisi del codice sono diversi rispetto agli errori e agli avvisi del compilatore in quanto durante l'analisi del codice vengono cercati modelli di codice specifici che risultano validi ma che potrebbero causare problemi a te o ad altre persone che usano il codice.

## <a name="configure-rule-sets-for-a-project"></a>Configurare i set di regole per un progetto

1. Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il nome del progetto e quindi scegliere **proprietà**.

2. I passaggi seguenti sono facoltativi:

    1. Nel **Configuration** e **piattaforma** elenchi, scegliere la piattaforma di destinazione e configurazione di compilazione.

    2. Per impostazione predefinita, l'analisi del codice non segnala gli avvisi del codice generato automaticamente da strumenti esterni. Per visualizzare gli avvisi del codice generato, deselezionare il **non visualizzare i risultati dal codice generato** casella di controllo.

        > [!NOTE]
        > Questa opzione non elimina errori di analisi del codice e gli avvisi del codice generato quando gli errori e gli avvisi vengono visualizzati nei moduli e nei modelli. È possibile visualizzare e gestire il codice sorgente per un modulo o un modello.

3. Per eseguire l'analisi del codice ogni volta che il progetto viene compilato con la configurazione selezionata, selezionare la **Attiva analisi codice per C/C++ in fase di compilazione** casella di controllo. È anche possibile eseguire manualmente l'analisi del codice aprendo il **Analyze** menu e scegliendo **Esegui analisi del codice** *NomeProgetto*.

4. Nel **eseguire questo set di regole** elenco, effettuare una delle operazioni seguenti:

    - Scegliere il set di regole che si desidera usare.

    - Scegli  **\<Sfoglia >** per specificare set di una regola personalizzata esistente non incluso nell'elenco.

    - Definire un [set di regole personalizzate](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Set di regole standard C/C++

Visual Studio include due set standard di regole per il codice nativo:

|Set di regole|Descrizione|
|--------------|-----------------|
|Regole minime native Microsoft|Questo set di regole è incentrato sui problemi più critici del codice nativo, inclusi i potenziali problemi di sicurezza e gli arresti anomali delle applicazioni. È necessario includere questo set di regole in qualsiasi set di regole personalizzate create per i progetti nativi.|
|Regole consigliate native Microsoft|Questo set di regole copre un'ampia gamma di problemi. Include tutte le regole in Regole minime native Microsoft.|

## <a name="run-code-analysis"></a>Eseguire l'analisi del codice

Nella pagina di analisi del codice delle pagine delle proprietà del progetto è possibile configurare l'analisi del codice per eseguirla ogni volta che si compila il progetto. È inoltre possibile eseguire manualmente l'analisi del codice.

Per eseguire l'analisi del codice su una soluzione:

- Dal menu **Genera** scegliere **Esegui analisi del codice sulla soluzione**.

Per eseguire l'analisi del codice su un progetto:

1. In Esplora soluzioni scegliere il nome del progetto.

2. Nel **compilare** menu, scegliere **Esegui analisi del codice** *nome progetto*.

   Il progetto o la soluzione vengono compilati e viene eseguita l'analisi del codice. I risultati vengono visualizzati nell'elenco errori.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analizzare e risolvere gli avvisi dell'analisi del codice

Per analizzare un avviso specifico, scegliere il titolo dell'avviso nell'elenco errori. L'avviso si espande per visualizzare informazioni aggiuntive sul problema. Se possibile, l'analisi del codice consente di visualizzare i numeri di riga e la logica di analisi che ha portato all'avviso. Per informazioni dettagliate sull'avviso, incluse le possibili soluzioni al problema, scegliere l'ID di avviso per visualizzare il corrispondente argomento della Guida in linea.

Quando si seleziona un avviso, la riga di codice che ha causato l'avviso viene evidenziata nell'editor del codice di Visual Studio.

Dopo aver compreso il problema, è possibile risolverlo nel codice. Quindi, rieseguire l'analisi di codice per assicurarsi che l'avviso non viene più visualizzata nell'elenco degli errori e che la correzione non generi gli avvisi di nuovo.

## <a name="suppress-code-analysis-warnings"></a>Non visualizzare gli avvisi dell'analisi codice

In alcuni casi potresti decidere di non correggere un avviso di analisi del codice. Puoi decidere che risolvere il problema richiede un'eccessiva ricodificazione relativamente alla probabilità che il problema si ripresenti in qualsiasi implementazione realistica del codice. Oppure potresti ritenere che l'analisi utilizzata nell'avviso sia inadeguata per il contesto specifico. È possibile eliminare gli avvisi in modo che non vengano più visualizzati nell'elenco errori.

Per eliminare un avviso:

1. Se le informazioni dettagliate non sono visualizzate, scegliere il titolo dell'avviso per espanderlo.

2. Scegliere il collegamento **Azioni** nella parte inferiore dell'avviso.

3. Scegli **Elimina messaggio** e quindi scegliere **In origine**.

   L'eliminazione di un messaggio inserisce `#pragma warning (disable:[warning ID])` che elimina l'avviso per la riga di codice.

## <a name="create-work-items-for-code-analysis-warnings"></a>Creare elementi di lavoro per il codice gli avvisi dell'analisi

È possibile usare la funzionalità di gestione degli elementi di lavoro per registrare bug da Visual Studio. Per usare questa funzionalità, collegarsi a un'istanza di Team Foundation Server.

**Per creare un elemento di lavoro per uno o più avvisi del codice C/C++**

1. Nell'elenco errori, espandere e selezionare l'avviso.

2. Nel menu di scelta rapida per gli avvisi, scegliere **Crea elemento di lavoro**, quindi scegliere il tipo di elemento di lavoro.

3. Visual Studio crea un singolo elemento di lavoro per gli avvisi selezionati e visualizza l'elemento di lavoro in una finestra del documento dell'IDE.

4. Aggiungere eventuali informazioni aggiuntive e quindi scegliere **Salva elemento di lavoro**.

## <a name="search-and-filter-code-analysis-results"></a>Cercare e filtrare i risultati dell'analisi codice

Puoi effettuare una ricerca in lunghi elenchi di messaggi di avviso e filtrare gli avvisi nelle soluzioni composte da più progetti.

- **Per filtrare gli avvisi per titolo o id avviso**: Immettere la parola chiave nella casella di ricerca.

- **Per filtrare gli avvisi per gravità**: Per impostazione predefinita, ai messaggi di analisi codice viene assegnato un livello di gravità **avviso**. È possibile assegnare la gravità di una o più messaggi come **errore** in una regola personalizzata impostata. Nel **gravità** della colonna della **elenco errori**, scegliere la freccia a discesa e quindi sull'icona del filtro. Scegli **avviso** oppure **errore** per visualizzare solo i messaggi che vengono assegnati il rispettivo livello di gravità. Scegli **Seleziona tutto** per visualizzare tutti i messaggi.

## <a name="see-also"></a>Vedere anche

[Analisi del codice per C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)