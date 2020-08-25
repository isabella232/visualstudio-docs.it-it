---
title: Usare l'editor set di regole di analisi codice
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 796818d376df477df84f845b5b0a17ace60bd1f2
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801542"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Usare l'editor set di regole di analisi del codice

Editor set di regole di analisi codice consente di specificare le regole incluse in un set di regole personalizzate e di impostare la gravità delle violazioni delle regole.

Nella tabella seguente vengono illustrate le opzioni di gravità:

|Azione (gravità)|Descrizione|
|-|-|
|Avviso|Genera un avviso nel **Elenco errori** e anche in fase di compilazione.|
|Errore|Genera un errore nel **Elenco errori** e anche in fase di compilazione.|
|Info|Genera un messaggio nel **Elenco errori**.|
|Nascosto|La violazione non è visibile all'utente. Tuttavia, l'IDE riceve una notifica della violazione.|
|nessuno|La regola è stata eliminata. Il comportamento è lo stesso di se la regola è stata rimossa dal set di regole.|

Nell'editor vengono visualizzate le regole in una struttura ad albero che raggruppa le regole in base a un campo del set di regole specificato. Per aggiungere o rimuovere regole da un set di regole, eseguire uno o più dei passaggi seguenti:

- Selezionare o deselezionare la casella di controllo del nodo gruppo per aggiungere o rimuovere tutte le regole del gruppo. Quando si seleziona un gruppo, tutte le regole vengono impostate sull'azione di **avviso** .

   > [!TIP]
   > È possibile modificare la modalità di raggruppamento delle regole nell'elenco a discesa **Raggruppa per** .

- Nel campo **azione** di un gruppo specificare l'azione da applicare a tutte le regole del gruppo.

- Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo relativa a una regola, la regola viene impostata sull'azione di **avviso** .

## <a name="toolbar"></a>Barra degli strumenti

È possibile utilizzare la barra degli strumenti dell'editor set di regole per raggruppare, filtrare e cercare i dati visualizzati nella griglia del set di regole.

Nella tabella seguente vengono descritti i controlli della barra degli strumenti dell'editor set di regole.

|Controllo Toolbar|Descrizione|
|---------------------|-----------------|
|**Espandi tutto**|Mostra le regole in tutti i gruppi.|
|**Comprimi tutto**|Nasconde le regole in tutti i gruppi.|
|**Raggruppa per**|Specifica il campo in base al quale vengono raggruppate le regole. Fare clic **\<None>** per visualizzare le regole senza gruppi.|
|**Opzioni colonne**|Specifica i campi della regola da visualizzare.|
|**Nascondi regole che non si applicano alla soluzione corrente**|Consente di visualizzare o nascondere regole che non sono dello stesso tipo di destinazione della soluzione.|
|**Mostra regole che possono generare errori di analisi del codice**|Consente di visualizzare o nascondere le regole a cui è stata assegnata l'azione di errore.|
|**Mostra regole che possono generare avvisi di analisi del codice**|Consente di visualizzare o nascondere le regole a cui è stata assegnata l'azione di avviso.|
|**Mostra regole non abilitate**|Consente di visualizzare o nascondere le regole a cui è stata assegnata l'azione nessuna.|
|**Aggiungi o Rimuovi set di regole figlio**|Aggiunge o rimuove le regole nei set di regole selezionati.|
|**Regole di ricerca**|Cerca tutti i valori di campo per la stringa specificata.|

## <a name="rule-set-fields"></a>Campi del set di regole

I campi del set di regole visualizzano informazioni su un set di regole e possono essere utilizzati per ordinare e raggruppare l'elenco di regole. Per visualizzare o nascondere i campi, selezionare **Opzioni colonne** sulla barra degli strumenti Editor set di regole, quindi selezionare o deselezionare le caselle di controllo dei campi da visualizzare o nascondere.

Nella tabella seguente vengono descritti i campi di un set di regole:

|Campo|Descrizione|
|-----------|-----------------|
|**ID**|Identificatore della regola.|
|**Categoria**|Oltre all'appartenenza ai set di regole, le regole di analisi del codice sono raggruppate per categoria. Per altre informazioni, vedere [avvisi di analisi del codice](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nome**|Titolo della regola.|
|**Spazio dei nomi**|Spazio dei nomi della regola.|
|**Tipo di destinazione**|Indica se la regola è per il codice nativo, gestito o del database.|
|**Azione**|Azione eseguita quando la regola viene violata in un'esecuzione dell'analisi del codice. È possibile modificare il campo **azione** .|
|**Set di regole di origine**|Set di regole che contiene la regola.|

## <a name="sort-and-filter-rule-sets"></a>Ordinare e filtrare i set di regole

Dalle intestazioni di colonna della griglia del set di regole è possibile ordinare e filtrare le regole in base ai valori del campo.

- Per ordinare gli elenchi dei set di regole, selezionare l'intestazione di colonna del campo in base al quale si desidera eseguire l'ordinamento. Se i set di regole sono raggruppati, ogni gruppo viene ordinato singolarmente.

- Per filtrare i set di regole in base al valore di un campo, selezionare il pulsante filtro nell'intestazione di colonna del campo in base al quale si desidera filtrare. Selezionare le caselle di controllo dei valori che si desidera visualizzare e deselezionare le caselle di controllo dei valori che si desidera nascondere.

## <a name="see-also"></a>Vedere anche

- [Creare un set di regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md)
