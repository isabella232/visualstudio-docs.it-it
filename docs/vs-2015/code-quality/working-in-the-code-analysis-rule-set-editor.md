---
title: Utilizzo dell'editor set di regole di analisi del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621514"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Utilizzo dell'editor set di regole di analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor set di regole di analisi codice consente di specificare le regole incluse in un set di regole personalizzate e di specificare l'azione. È inoltre possibile specificare l'azione da eseguire quando l'analisi del codice rileva una violazione della regola.

|Azione|Descrizione|
|------------|-----------------|
|**Warning**|Genera un avviso nella finestra **Elenco errori** .|
|**Erroree**|Genera un errore nella finestra di **Elenco errori** .|
|**Nessuno**|Disabilita la regola.|

 Nell'editor vengono visualizzate le regole in una struttura ad albero che raggruppa le regole in base a un campo del set di regole specificato. Per aggiungere o rimuovere regole da un set di regole, eseguire uno o più dei passaggi seguenti:

- Selezionare o deselezionare la casella di controllo del nodo gruppo per aggiungere o rimuovere tutte le regole del gruppo. Quando si seleziona un gruppo, tutte le regole vengono impostate sull'azione di **avviso** .

- Fare clic sul campo **azione** di un gruppo, quindi specificare l'azione da applicare a tutte le regole del gruppo.

- Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo relativa a una regola, la regola viene impostata sull'azione di avviso.

## <a name="rule-set-editor-toolbar"></a>Barra degli strumenti Editor set di regole
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
 I campi del set di regole visualizzano informazioni su un set di regole e possono essere utilizzati per ordinare e raggruppare l'elenco di regole. Per visualizzare o nascondere i campi, fare clic su **Opzioni colonne** sulla barra degli strumenti dell'editor set di regole, quindi selezionare o deselezionare le caselle di controllo dei campi da visualizzare o nascondere.

 Nella tabella seguente vengono descritti i campi di un set di regole.

|Campo|Descrizione|
|-----------|-----------------|
|**ID**|Identificatore della regola.|
|**Categoria**|Oltre all'appartenenza ai set di regole, le regole di analisi del codice sono raggruppate per categoria. Per ulteriori informazioni, vedere l' [analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Titolo della regola.|
|**Spazio dei nomi**|Spazio dei nomi della regola.|
|**Tipo di destinazione**|Indica se la regola è per il codice nativo, gestito o del database.|
|**Azione**|Azione eseguita quando la regola viene violata in un'esecuzione dell'analisi del codice.<br /><br /> **Avviso** : genera un avviso.<br /><br /> **Errore** : genera un errore.<br /><br /> **None** : Disabilita la regola.<br /><br /> È possibile modificare il campo azione. L'impostazione del valore su None equivale alla cancellazione della casella di controllo per la regola.|
|**Set di regole di origine**|Set di regole che contiene la regola.|

## <a name="sorting-and-filtering-rule-sets"></a>Ordinamento e filtro di set di regole
 Dalle intestazioni di colonna della griglia del set di regole è possibile ordinare e filtrare le regole in base ai valori del campo.

- Per ordinare gli elenchi di set di regole, fare clic sull'intestazione di colonna del campo in base al quale si desidera eseguire l'ordinamento. Se i set di regole sono raggruppati, ogni gruppo viene ordinato singolarmente.

- Per filtrare i set di regole in base al valore di un campo, fare clic sul pulsante filtro nell'intestazione di colonna del campo in base al quale si desidera filtrare. Selezionare le caselle di controllo dei valori che si desidera visualizzare e deselezionare le caselle di controllo dei valori che si desidera nascondere.
