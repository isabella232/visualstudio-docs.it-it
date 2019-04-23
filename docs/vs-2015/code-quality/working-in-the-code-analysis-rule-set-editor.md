---
title: Utilizzo di regole di analisi codice Editor Set | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 57d3c21371cc824573e29657d0b41253e556f4c3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072253"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Utilizzo dell'editor set di regole di analisi del codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'editor set di regole di analisi del codice consente di specificare le regole incluse in un set di regole personalizzate e per specificare l'azione. È anche possibile specificare l'azione da intraprendere quando l'analisi del codice rileva una violazione della regola.  
  
|Operazione|Descrizione|  
|------------|-----------------|  
|**Avviso**|Genera un avviso nel **elenco errori** finestra.|  
|**Erroree**|Genera un errore nel **elenco errori** finestra.|  
|**None**|Disabilita la regola.|  
  
 L'editor visualizza le regole in una struttura ad albero che set di gruppi di regole da una regola di campo specificato. Per aggiungere o rimuovere le regole da un set di regole, eseguire una o più delle operazioni seguenti:  
  
- Selezionare o deselezionare la casella di controllo del nodo di gruppo per aggiungere o rimuovere tutte le regole del gruppo. Quando si seleziona un gruppo, tutte le regole sono impostate il **avviso** azione.  
  
- Fare clic sui **azione** campo di un gruppo, quindi specificare l'azione da applicare a tutte le regole del gruppo.  
  
- Selezionare o deselezionare la casella di controllo per una singola regola. Quando si seleziona la casella di controllo per una regola, la regola è impostata per l'azione di avviso.  
  
## <a name="rule-set-editor-toolbar"></a>Editor barra degli strumenti del Set di regole  
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
  
## <a name="rule-set-fields"></a>Campi di Set di regole  
 Set di regole campi visualizzare informazioni su una regola impostata e possono essere utilizzate per ordinare e raggruppare l'elenco delle regole. Per visualizzare o nascondere i campi, fare clic su **opzioni di colonna** sulla regola impostata sulla barra degli strumenti dell'editor e quindi selezionare o deselezionare le caselle di controllo dei campi per mostrare o nascondere.  
  
 Nella tabella seguente vengono descritti i campi di un set di regole.  
  
|Campo|Descrizione|  
|-----------|-----------------|  
|**ID**|L'identificatore della regola.|  
|**Categoria**|Oltre alla loro l'appartenenza al set di regole, regole di analisi del codice vengono inoltre raggruppate per categoria. Per altre informazioni, vedere [analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Il titolo della regola.|  
|**Spazio dei nomi**|Lo spazio dei nomi della regola.|  
|**Tipo di destinazione**|Indica se la regola è per nativo, gestito o codice di database.|  
|**Azione**|L'azione eseguita quando la regola viene violata in un'esecuzione dell'analisi codice.<br /><br /> **Avviso** -genera un avviso.<br /><br /> **Errore** -verrà generato un errore.<br /><br /> **Nessuno** -disabilita la regola.<br /><br /> È possibile modificare il campo dell'azione. Impostare il valore su None è equivale a deselezionare la casella di controllo per la regola.|  
|**Set regole origine**|Il set di regole che contiene la regola.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Ordinare e filtrare i set di regole  
 Delle intestazioni di colonna della griglia set di regole, è possibile ordinare e filtrare le regole in base ai valori del campo.  
  
- Per ordinare gli elenchi di set di regole, fare clic sull'intestazione di colonna del campo da cui si desidera ordinare. Se vengono raggruppati i set di regole, ogni gruppo viene ordinato singolarmente.  
  
- Per filtrare i set di regole per il valore di un campo, fare clic sul pulsante filtro nell'intestazione di colonna del campo da cui si desidera filtrare. Selezionare le caselle di controllo dei valori che si desidera visualizzare e deselezionare le caselle di controllo dei valori che si desidera nascondere.
