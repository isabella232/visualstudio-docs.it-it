---
title: Usare l'Editor di Set di regole di analisi codice
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 719d8f1e11365de0b864f41f54546fb4bfc64cd2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937219"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Usare l'editor di set di regole di analisi codice

La regola di analisi codice imposta editor consente di che specificare le regole incluse in una regola personalizzata impostata e impostare la gravità di violazioni delle regole.

Nella tabella seguente mostra le opzioni di gravità:

|Azione (gravità)|Descrizione|
|-|-|
|Avviso|Genera un avviso nel **elenco errori** e anche in fase di compilazione.|
|Error|Genera un errore nel **elenco errori** e anche in fase di compilazione.|
|Info|Genera un messaggio nel **elenco errori**.|
|Hidden|La violazione non è visibile all'utente. L'IDE viene informato della violazione, tuttavia.|
|nessuno|La regola viene eliminata. Il comportamento è lo stesso come se la regola è stato rimosso dal set di regole.|

L'editor visualizza le regole in una struttura ad albero che set di gruppi di regole da una regola di campo specificato. Per aggiungere o rimuovere le regole da un set di regole, eseguire una o più delle operazioni seguenti:

- Selezionare o deselezionare la casella di controllo del nodo di gruppo per aggiungere o rimuovere tutte le regole del gruppo. Quando si seleziona un gruppo, tutte le regole sono impostate il **avviso** azione.

   > [!TIP]
   > È possibile modificare come le regole sono raggruppate nel **Raggruppa** elenco a discesa.

- Fare clic sui **azione** campo di un gruppo, quindi specificare l'azione da applicare a tutte le regole del gruppo.

- Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo per una regola, la regola è impostata per l'azione di avviso.

## <a name="toolbar"></a>ToolBar

È possibile utilizzare la barra degli strumenti dell'editor set di regole per raggruppare, filtrare e cercare i dati visualizzati nella griglia set di regole.

Nella tabella seguente vengono descritti i controlli sulla barra degli strumenti dell'editor set di regole.

|Controllo ToolBar|Descrizione|
|---------------------|-----------------|
|**Espandi tutto**|Vengono illustrate le regole in tutti i gruppi.|
|**Comprimi tutto**|Consente di nascondere le regole in tutti i gruppi.|
|**Group By**|Specifica il campo mediante il quale le regole sono raggruppate. Fare clic su  **\<None >** per mostrare le regole senza gruppi.|
|**Opzioni colonne**|Specifica i campi di regola da visualizzare.|
|**Nascondi le regole che non si applicano alla soluzione corrente**|Mostra o nasconde le regole che non sono dello stesso tipo di destinazione della soluzione.|
|**Mostra regole che possono generare errori di analisi del codice**|Mostra o nasconde le regole che vengono assegnate l'azione di errore.|
|**Mostra regole che possono generare avvisi di analisi del codice**|Mostra o nasconde le regole di cui sono assegnate l'azione di avviso.|
|**Mostra regole che non sono abilitate**|Mostra o nasconde le regole che vengono assegnate a nessun azione.|
|**Aggiungere o rimuovere set di regole figlio**|Aggiunge o rimuove le regole nei set di regole selezionato.|
|**Cerca regole**|Cerca in tutti i valori dei campi per la stringa specificata.|

## <a name="rule-set-fields"></a>Campi del set di regole

Campi di set di regole visualizzano informazioni su un set di regole e possono essere utilizzati per ordinare e raggruppare l'elenco delle regole. Per visualizzare o nascondere i campi, selezionare **opzioni di colonna** sulla regola impostata sulla barra degli strumenti dell'editor e quindi selezionare o deselezionare le caselle di controllo dei campi per mostrare o nascondere.

Nella tabella seguente vengono descritti i campi di un set di regole:

|Campo|Descrizione|
|-----------|-----------------|
|**ID**|L'identificatore della regola.|
|**Categoria**|Oltre alla loro l'appartenenza al set di regole, regole di analisi del codice vengono inoltre raggruppate per categoria. Per altre informazioni, vedere [gli avvisi dell'analisi del codice](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Il titolo della regola.|
|**Spazio dei nomi**|Lo spazio dei nomi della regola.|
|**Tipo di destinazione**|Indica se la regola è per nativo, gestito o codice di database.|
|**Azione**|L'azione eseguita quando la regola viene violata in un'esecuzione dell'analisi codice. È possibile modificare il **azione** campo.|
|**Set regole origine**|Il set di regole che contiene la regola.|

## <a name="sort-and-filter-rule-sets"></a>Ordina e filtra set di regole

Delle intestazioni di colonna della griglia set di regole, è possibile ordinare e filtrare le regole in base ai valori del campo.

- Per ordinare gli elenchi di set di regole, fare clic sull'intestazione di colonna del campo da cui si desidera ordinare. Se vengono raggruppati i set di regole, ogni gruppo viene ordinato singolarmente.

- Per filtrare i set di regole per il valore di un campo, fare clic sul pulsante filtro nell'intestazione di colonna del campo da cui si desidera filtrare. Selezionare le caselle di controllo dei valori che si desidera visualizzare e deselezionare le caselle di controllo dei valori che si desidera nascondere.

## <a name="see-also"></a>Vedere anche

- [Creare un set di regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md)