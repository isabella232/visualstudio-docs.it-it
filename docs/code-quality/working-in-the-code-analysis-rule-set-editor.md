---
title: Usare l'editor set di regole di analisi codice
ms.date: 04/04/2018
description: Informazioni su come modificare e visualizzare i set di regole in Visual Studio. Informazioni su come impostare la gravità delle regole, specificare le regole in un set personalizzato e modificare i dati nella griglia del set di regole.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 724d5c541d90eedc335aaf840eea389510b6d8dd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631794"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Usare l'editor del set di regole di analisi del codice

L'editor del set di regole di analisi del codice consente di specificare le regole incluse in un set di regole personalizzate e di impostare la gravità delle violazioni delle regole.

La tabella seguente illustra le opzioni di gravità:

|Azione (gravità)|Descrizione|
|-|-|
|Avviso|Genera un avviso **nell'Elenco errori e** anche in fase di compilazione.|
|Errore|Genera un errore **nell'Elenco errori e** anche in fase di compilazione.|
|Info|Genera un messaggio in **Elenco errori**.|
|Nascosto|La violazione non è visibile all'utente. L'IDE, tuttavia, viene informato della violazione.|
|Nessuno|La regola viene eliminata. Il comportamento è identico a quello che si verifica se la regola è stata rimossa dal set di regole.|

L'editor visualizza le regole in una struttura ad albero che raggruppa le regole in base a un campo del set di regole specificato. Per aggiungere o rimuovere regole da un set di regole, eseguire uno o più dei passaggi seguenti:

- Selezionare o deselezionare la casella di controllo del nodo del gruppo per aggiungere o rimuovere tutte le regole nel gruppo. Quando si seleziona un gruppo, tutte le regole vengono impostate **sull'azione Avviso.**

   > [!TIP]
   > È possibile modificare la modalità di raggruppamento delle regole nell'elenco **a** discesa Raggruppa per.

- Fare clic **sul campo** Azione di un gruppo e specificare l'azione da applicare a tutte le regole del gruppo.

- Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo per una regola, la regola viene impostata **sull'azione Avviso.**

## <a name="toolbar"></a>Barra degli strumenti

È possibile usare la barra degli strumenti dell'editor del set di regole per raggruppare, filtrare ed eseguire ricerche nei dati visualizzati nella griglia del set di regole.

Nella tabella seguente vengono descritti i controlli sulla barra degli strumenti dell'editor del set di regole.

|Controllo Barra degli strumenti|Descrizione|
|---------------------|-----------------|
|**Espandi tutto**|Mostra le regole in tutti i gruppi.|
|**Comprimi tutto**|Nasconde le regole in tutti i gruppi.|
|**Raggruppa per**|Specifica il campo in base al quale vengono raggruppate le regole. Fare **\<None>** clic per visualizzare le regole senza gruppi.|
|**Opzioni colonne**|Specifica i campi della regola da visualizzare.|
|**Nascondere le regole che non si applicano alla soluzione corrente**|Mostra o nasconde le regole che non sono dello stesso tipo di destinazione della soluzione.|
|**Mostra regole che possono generare Code Analysis errori**|Mostra o nasconde le regole a cui è assegnata l'azione Errore.|
|**Visualizzare le regole che possono generare Code Analysis avvisi**|Mostra o nasconde le regole a cui è assegnata l'azione Avviso.|
|**Mostra regole non abilitate**|Mostra o nasconde le regole a cui è assegnata l'azione Nessuna.|
|**Aggiungere o rimuovere set di regole figlio**|Aggiunge o rimuove le regole nei set di regole selezionati.|
|**Regole di ricerca**|Cerca in tutti i valori di campo la stringa specificata.|

## <a name="rule-set-fields"></a>Campi del set di regole

I campi del set di regole visualizzano informazioni su un set di regole e possono essere usati per ordinare e raggruppare l'elenco di regole. Per visualizzare o nascondere i campi, **selezionare** Opzioni colonne sulla barra degli strumenti dell'editor del set di regole e quindi selezionare o deselezionare le caselle di controllo dei campi da visualizzare o nascondere.

La tabella seguente descrive i campi di un set di regole:

|Campo|Descrizione|
|-----------|-----------------|
|**ID**|Identificatore della regola.|
|**Categoria**|Oltre all'appartenenza ai set di regole, anche le regole di analisi del codice vengono raggruppate per categoria. Per altre informazioni, vedere [Avvisi di analisi codice.](/dotnet/fundamentals/code-analysis/quality-rules/index)|
|**Nome**|Titolo della regola.|
|**Namespace**|Spazio dei nomi della regola.|
|**Tipo di destinazione**|Indica se la regola è per codice nativo, gestito o di database.|
|**Azione**|Azione eseguita quando la regola viene violata in un'esecuzione dell'analisi del codice. È possibile modificare il **campo** Azione.|
|**Set di regole di origine**|Set di regole che contiene la regola.|

## <a name="sort-and-filter-rule-sets"></a>Ordinare e filtrare i set di regole

Dalle intestazioni di colonna della griglia del set di regole è possibile ordinare e filtrare le regole in base ai valori del campo.

- Per ordinare gli elenchi di set di regole, selezionare l'intestazione di colonna del campo in base al quale si desidera eseguire l'ordinamento. Se i set di regole sono raggruppati, ogni gruppo viene ordinato singolarmente.

- Per filtrare i set di regole in base al valore di un campo, selezionare il pulsante di filtro nell'intestazione di colonna del campo in base al quale si vuole filtrare. Selezionare le caselle di controllo dei valori da visualizzare e deselezionare le caselle di controllo dei valori da nascondere.

## <a name="see-also"></a>Vedi anche

- [Creare un set di regole personalizzato](../code-quality/how-to-create-a-custom-rule-set.md)
