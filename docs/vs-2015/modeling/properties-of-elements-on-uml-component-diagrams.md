---
title: Proprietà degli elementi nei diagrammi dei componenti UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671453"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Proprietà degli elementi nei diagrammi dei componenti UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma dei componenti UML ogni elemento nel diagramma include proprietà. Per visualizzare le proprietà di un elemento, fare clic con il pulsante destro del mouse sull'elemento nel diagramma o in **Esplora modelli UML** e quindi scegliere **Proprietà**. Le proprietà vengono visualizzate nella finestra **Proprietà** .

> [!NOTE]
> Questo argomento illustra le proprietà degli elementi nei diagrammi dei componenti UML. Per altre informazioni su come leggere i diagrammi dei componenti UML, vedere [diagrammi dei componenti UML:](../modeling/uml-component-diagrams-reference.md)informazioni di riferimento. Per altre informazioni su come creare diagrammi dei componenti UML, vedere [diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Proprietà degli elementi

|proprietà|Impostazione predefinita|Elemento|Descrizione|
|--------------|-------------|-------------|-----------------|
|**Nome**|Nome predefinito|All|Identifica l'elemento.|
|**Nome completo**|Spazio dei nomi :: Nome|All|Identifica l'elemento in modo univoco.<br /><br /> Il nome di un componente o di un tipo è preceduto dal nome qualificato del pacchetto che lo contiene.<br /><br /> Il nome di una parte o di una porta è preceduto dal nome qualificato del componente che lo possiede.|
|**Elementi di lavoro**|0 elementi associati|All|Numero di elementi di lavoro associati a questo elemento. Per associare elementi di lavoro, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|
|**Descrizione**|(nessuno)|All|Qui è possibile inserire note generali sull'elemento.|
|**Colore**|(impostazione predefinita per il tipo)|Componente, parte, delega, assembly parti|Colore della forma. A differenza delle altre proprietà, si tratta del colore della forma anziché dell'elemento di modello visualizzato dalla forma.|
|**Viene creata indirettamente**|True|Componente|Il componente esiste solo come elemento di progettazione. In fase di esecuzione esistono solo le relative parti.|
|**È astratto**|False|Componente|La definizione del componente può essere usata solo come generalizzazione da cui possono essere specializzati altri componenti.|
|**Visibilità**|Public|Componente, parte, porta|**Public** -visibile globalmente.<br /><br /> **Pacchetto** : visibile all'interno del pacchetto.<br /><br /> **Privato** : visibile all'interno del componente proprietario.<br /><br /> **Protected** : visibile ai componenti derivati dal proprietario.|
|**Type**|Tipo alla creazione|Parte<br /><br /> Porta|Il tipo di una parte è un componente o una classe.<br /><br /> Il tipo di una porta è un'interfaccia.|
|**Molteplicità**|1|Parte<br /><br /> Porta|Indica il numero di istanze del tipo specificato che fanno parte del componente padre.<br /><br /> `1`: esattamente una.<br /><br /> `0..1`: una o nessuna.<br /><br /> `*`: una raccolta di un numero qualsiasi di istanze.<br /><br /> `n..m`: una raccolta di n-m istanze.|
|**Comportamento**|False|Porta|Se true, i messaggi a questa porta vengono gestiti da attività o operazioni descritte come parte del componente, invece che delle parti.|
|**Servizio is**|False|Porta|Se true, la porta fa parte dell'interfaccia pubblicata di questo componente.|
|**LinkedPackage**|Modello|Diagramma|Spazio dei nomi predefinito per gli elementi aggiunti a questo diagramma.|

## <a name="see-also"></a>Vedere anche
 [Diagrammi caso d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md) [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)
