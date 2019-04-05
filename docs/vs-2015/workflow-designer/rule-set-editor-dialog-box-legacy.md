---
title: (Legacy) finestra di dialogo Editor Set di regole | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e259328b2c9b7e2abcd5decead3560cb184fa930
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969450"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Finestra di dialogo Editor set di regole (legacy)
Questo argomento viene descritto come usare il **Editor Set di regole** nella finestra di dialogo legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Il **Editor Set di regole** finestra di dialogo consente di creare e modificare [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) regola set, che vengono serializzati in un file con estensione rules.  
  
> [!NOTE]
>  Se si desidera aprire il file con estensione rules con il **Editor XML con codifica**, è necessario chiudere la finestra di progettazione associata per il flusso di lavoro o attività.  
  
 Per informazioni su come accedere al **Editor Set di regole** finestra di dialogo, vedere [come: Creare un Set di regole di attività PolicyActivity (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  L'editor delle regole della [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy che viene usato per fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] non supporta il multitargeting.  
  
 La tabella seguente descrive gli elementi dell'interfaccia utente di **Editor Set di regole** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Aggiungi regola**|Aggiunge una nuova definizione della regola nuova nell’insieme di regole.|  
|**Eliminazione**|Elimina la regola selezionata dall’insieme di regole.|  
|**Il concatenamento**|Specifica quale tipo di concatenamento diretto usare con l’insieme di regole. Le opzioni disponibili sono:<br /><br /> -   **Concatenamento completo**, che consente di usare tutti i meccanismi di concatenamento diretto: implicito, con attribuzione del metodo ed esplicito usando un' **Update** (funzione).<br />-   **Sequenziale**, che consente di non usare alcun concatenamento.<br />-   **Solo aggiornamento esplicito**, che consente di eseguire soltanto concatenamento diretto sulle **Update** azioni.<br /><br /> Per altre informazioni sul concatenamento, vedere [usando l'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Name**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per nome.|  
|**Priorità**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per priorità.|  
|**Nuova valutazione**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per tipo di rivalutazione.|  
|**Anteprima della regola**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per anteprima di una condizione della regola e delle azioni.|  
|**Nome:**|Immettere il nome della regola.|  
|**Priorità:**|Immettere una priorità per la regola. La priorità predefinita è 0.|  
|**Nuova valutazione:**|Specifica quale tipo di rivalutazione della regola usare con la regola. Le opzioni disponibili sono:<br /><br /> -   **Sempre**, in modo che la regola sia rivalutata in base alle esigenze.<br />-   **Mai**, in modo che la regola sia mai rivalutata. In questo caso una regola viene eseguita solo una volta.|  
|**Active**|Selezionare per rendere attiva la regola.|  
|**Condizione:**|Immettere un'espressione per la condizione della regola. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|  
|**Azioni Then:**|Immettere l'espressione per azioni THEN. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|  
|**Azioni Else:**|Immettere l'espressione per azioni ELSE. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|  
|**OK**|Fare clic per salvare l’insieme di regole in un file con estensione rules.|  
  
 Per altre informazioni sui set di regole, vedere [usando l'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Immissione di espressioni di condizioni e azioni  
 È possibile immettere espressioni per la condizione e Then ed Else azioni, ad esempio testo contenuto nella loro rispettive finestre nel **Editor Set di regole** nella finestra di dialogo. È possibile digitare **questo.** Nell'editor per fare riferimento a campi, proprietà e metodi usati nel flusso di lavoro, tramite un tipo di IntelliSense dei menu. In alternativa, è possibile digitare direttamente il nome di un membro del flusso di lavoro. È possibile richiamare metodi statici sui tipi a cui viene fatto riferimento digitando il nome della classe seguito dal nome del metodo.  
  
 È possibile aggiungere operatori logici alla condizione, ad esempio E, O e NON. È anche possibile aggiungere predicati. Un predicato è composto da un operatore binario e due operandi. Gli operatori binari supportati sono = =, >, \<, > =, e < =. Gli operandi supportati sono membri pubblici ai quali è stato assegnato un valore costante, una funzione aritmetica e un ambito.  
  
 È possibile specificare il tipo per il confronto, ed è possibile confrontare con **null** o una stringa vuota. È possibile annidare chiamate ai membri su una variabile contenente un tipo complesso, ad esempio, `this.Address.State == "WA"`.  
  
 Le espressioni supportano gli operatori seguenti:  
  
- operatori relazionali: ==, =, !=  
  
- Gli operatori di confronto: <, \<=, >, > =  
  
- Operatori aritmetici: +, - , *, /, MOD  
  
- Operatori logici: AND, &&, OR, &#124;&#124;, NOT, !  
  
- Operatori bit per bit: &,&#124;  
  
  La precedenza di operatori dell’espressione segue le regole di precedenza dell’operatore C#.  
  
  Per altre informazioni sulle condizioni, vedere [utilizzo delle condizioni nei flussi di lavoro](http://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Funzioni Halt e Aggiorna  
 **Azioni Then:** e **azioni Else:** espressioni supportano **Halt** e **Update** funzioni. Usare il **Halt** di funzione, digitare **Halt** in un **azione Then:** oppure **azione Else:** casella di testo. Il **Halt** azione causa l'esecuzione di set di regole arrestare immediatamente, e il controllo ritorna al codice chiamante. Si utilizza il **Update** funzione con il concatenamento in avanti.  
  
 Un' **Update** istruzione può essere espressa nell'editor in uno dei due moduli; entrambi i moduli vengono visualizzati nell'esempio seguente:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Per altre informazioni sull'uso **Update** con concatenamento diretto, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Vedere anche  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Finestra di dialogo Set di regola selezionare (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Uso delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)