---
title: Finestra di dialogo Editor set di regole (legacy) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce9e18a832ceceebc56e294023bc4ae3d06101cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663331"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Finestra di dialogo Editor set di regole (legacy)
In questo argomento viene descritto come utilizzare la finestra di dialogo **Editor set di regole** nella [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 La finestra di dialogo **Editor set di regole** viene utilizzata per creare e modificare i set di regole [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) , che vengono serializzati in un file con estensione rules.

> [!NOTE]
> Se si desidera aprire il file con estensione rules con l' **editor XML con codifica**, è innanzitutto necessario chiudere la finestra di progettazione associata per il flusso di lavoro o l'attività.

 Per informazioni su come accedere alla finestra di dialogo **Editor set di regole** , vedere [procedura: creare un set di regole PolicyActivity (legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> L'editor delle regole della [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy che viene usato per fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] non supporta il multitargeting.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **Editor set di regole** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Aggiungi regola**|Aggiunge una nuova definizione della regola nuova nell’insieme di regole.|
|**Eliminazione**|Elimina la regola selezionata dall’insieme di regole.|
|**Concatenamento**|Specifica quale tipo di concatenamento diretto usare con l’insieme di regole. Le opzioni disponibili sono:<br /><br /> -   **concatenamento completo**, che specifica di usare tutti i meccanismi di concatenamento diretto: implicito, attribuzione di metodi ed esplicita usando una funzione **Update** .<br />-   **sequenziale**, che specifica di non usare alcun concatenamento diretto.<br />-   **solo l'aggiornamento esplicito**, che specifica di eseguire il concatenamento diretto solo per le azioni di **aggiornamento** .<br /><br /> Per ulteriori informazioni sul concatenamento diretto, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|**Nome**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per nome.|
|**Priorità**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per priorità.|
|**Rivalutazione**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per tipo di rivalutazione.|
|**Anteprima della regola**|Intestazione di colonna dell’elenco dell’insieme di regole. Fare clic per ordinare l'elenco di regole per anteprima di una condizione della regola e delle azioni.|
|**Name:**|Immettere il nome della regola.|
|**Priorità**|Immettere una priorità per la regola. La priorità predefinita è 0.|
|**Rivalutazione**|Specifica quale tipo di rivalutazione della regola usare con la regola. Le opzioni disponibili sono:<br /><br /> -   **sempre**, che fa sì che la regola venga rivalutata in base alle esigenze.<br />-   **mai**, in modo che la regola non venga mai rivalutata. In questo caso una regola viene eseguita solo una volta.|
|**Active**|Selezionare per rendere attiva la regola.|
|**Condizione**|Immettere un'espressione per la condizione della regola. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|
|**Azioni Then:**|Immettere l'espressione per azioni THEN. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|
|**Azioni else:**|Immettere l'espressione per azioni ELSE. Per informazioni sulla sintassi dell'espressione, vedere la sessione riguardante l’immissione di espressioni di condizioni e azioni in questa pagina.|
|**Ok**|Fare clic per salvare l’insieme di regole in un file con estensione rules.|

 Per ulteriori informazioni sui set di regole, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>Immissione di espressioni di condizioni e azioni
 Immettere le espressioni per la condizione e le azioni Then e else come testo nelle rispettive caselle di testo nella finestra di dialogo **Editor set di regole** . È possibile digitare **questo.** nell'editor per fare riferimento a campi, proprietà e metodi usati nel flusso di lavoro usando un menu di tipo IntelliSense. In alternativa, è possibile digitare direttamente il nome di un membro del flusso di lavoro. È possibile richiamare metodi statici sui tipi a cui viene fatto riferimento digitando il nome della classe seguito dal nome del metodo.

 È possibile aggiungere operatori logici alla condizione, ad esempio E, O e NON. È anche possibile aggiungere predicati. Un predicato è composto da un operatore binario e due operandi. Gli operatori binari supportati sono = =, >, \<, > = e < =. Gli operandi supportati sono membri pubblici ai quali è stato assegnato un valore costante, una funzione aritmetica e un ambito.

 È possibile specificare il tipo per il confronto ed è possibile confrontarlo con un **valore null** o una stringa vuota. È possibile annidare chiamate ai membri su una variabile contenente un tipo complesso, ad esempio, `this.Address.State == "WA"`.

 Le espressioni supportano gli operatori seguenti:

- operatori relazionali: ==, =, !=

- Operatori di confronto: <, \< =, >, > =

- Operatori aritmetici: +, - , *, /, MOD

- Operatori logici: and, & & o, &#124; &#124;, not,!

- Operatori bit per bit: &,&#124;

  La precedenza di operatori dell’espressione segue le regole di precedenza dell’operatore C#.

  Per ulteriori informazioni sulle condizioni, vedere [utilizzo delle condizioni nei flussi di lavoro](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Funzioni Halt e Aggiorna
 **Azioni Then:** e **else Actions:** le espressioni supportano le funzioni **Halt** e **Update** . Per usare la funzione **Halt** , digitare **Halt** in una casella di testo azione **then:** oppure **azione else:** . L'azione **Halt** causa l'arresto immediato dell'esecuzione del set di regole e il controllo viene restituito al codice chiamante. Usare la funzione **Update** con il concatenamento diretto.

 Un'istruzione **Update** può essere espressa nell'editor in uno dei due formati seguenti: Nell'esempio seguente vengono illustrati entrambi i formati:

```
Update(this.Address.State)
Update("this/Address/State")
```

 Per ulteriori informazioni sull'utilizzo di **Update** con il concatenamento diretto, vedere [utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>Vedere anche
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) [finestra di dialogo Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [usando l'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004) [usando le condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)