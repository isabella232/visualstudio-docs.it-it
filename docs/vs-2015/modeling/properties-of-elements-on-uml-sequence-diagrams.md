---
title: Proprietà degli elementi nei diagrammi di sequenza UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671431"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Proprietà di elementi in diagrammi di sequenza UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma sequenza UML, ogni elemento del diagramma ha delle proprietà. Per visualizzare le proprietà di un elemento, fare clic con il pulsante destro del mouse sull'elemento nel diagramma o in **Esplora modelli UML** e quindi scegliere **Proprietà**. Le proprietà vengono visualizzate nella finestra **Proprietà** .

> [!NOTE]
> Questo argomento illustra le proprietà degli elementi nei diagrammi di sequenza UML. Per altre informazioni su come leggere i diagrammi di sequenza UML, vedere [diagrammi di sequenza UML: riferimenti](../modeling/uml-sequence-diagrams-reference.md). Per altre informazioni su come creare diagrammi di sequenza UML, vedere [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Proprietà degli elementi

|proprietà|Impostazione predefinita|Elemento|Descrizione|
|--------------|-------------|-------------|-----------------|
|**Nome**|Nome predefinito|All|Identifica l'elemento.|
|**Nome completo**|Pacchetto :: Nome|All|Identifica l'elemento in modo univoco. Preceduto dal nome completo del pacchetto che lo contiene.|
|**Elementi di lavoro**|0 elementi associati|All|Numero di elementi di lavoro associati a questo elemento. Per associare elementi di lavoro, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|
|**Descrizione**|(vuoto)|All|È possibile inserire note generali sull'elemento.|
|**Colore**|(valore predefinito per il tipo di elemento)|Linea di vita, messaggio|Colore della forma. Si tratta di una proprietà della forma, piuttosto che dell'elemento visualizzato.|
|**Type**|(vuoto)|Linea di vita|Tipo dell'istanza rappresentato dalla linea di vita.<br /><br /> Se nell'intestazione della linea di vita viene visualizzato un simbolo di riferimento, la classe o l'interfaccia sarà indicata separatamente in Esplora modelli UML e potrà essere visualizzata in un diagramma classi.|
|**Attore**|False|Linea di vita|Indica se la linea di vita rappresenta un utente, un dispositivo o un componente software esterno al componente oggetto del diagramma.|
|**Tipo**|**Completa** : messaggio con mittente e destinatario.<br /><br /> **Trovato** : messaggio con un mittente non specificato.<br /><br /> **Lost** : messaggio con un destinatario non specificato.|Messaggio|Indica le estremità di un messaggio associate a una linea di vita.<br /><br /> Questa proprietà non può essere modificata. Viene impostata quando si crea il messaggio.|
|**Ordinamento**|**AsynchCall** : messaggio asincrono.<br /><br /> **SynchCall** -un messaggio sincrono.<br /><br /> **Reply** : la parte restituita di un messaggio sincrono.<br /><br /> **CreateMessage** : messaggio di creazione dell'istanza.|Messaggio|Tipo di messaggio. Questa proprietà non può essere modificata. È determinata dallo strumento usato per creare il messaggio.|
|**Operazione**|(vuoto)|Messaggio|Metodo chiamato dal messaggio nella linea di vita dell'oggetto destinatario.<br /><br /> Visibile solo se la linea di vita dell'oggetto destinatario è collegata a un'interfaccia o una classe.|
|**Fa riferimento a**|Diagramma di sequenza|Utilizzo interazione|Diagramma di sequenza chiamato dall'utilizzo interazione.|
|**Operatore di interazione**|Impostato quando è stato usato il comando **Racchiudi tra**|Frammento combinato|Operatore rappresentato da questo frammento o questa raccolta di frammenti.|
|**Guard**|(vuoto)|Frammento combinato con due operandi di interazione|La sequenza nel frammento si verificherà solo se guard è true.<br /><br /> Per selezionare il frammento superiore di qualsiasi frammento combinato, fare clic sotto il titolo del frammento.|
|**Min, max**|(nessuna restrizione)|Ciclo frammento combinato|Numero minimo e massimo di volte in cui che viene eseguito il ciclo.|
|**Messaggi**|(vuoto)|Considera e<br /><br /> ignora frammenti combinati|Messaggi considerati o ignorati in questo frammento.|

## <a name="see-also"></a>Vedere anche
 [Diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md) [diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md) [descrivere il flusso di controllo con frammenti nei diagrammi di sequenza UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
