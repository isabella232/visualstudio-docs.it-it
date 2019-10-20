---
title: Proprietà di elementi in diagrammi caso di utilizzo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671411"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Proprietà di elementi in diagrammi caso d'uso UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma caso di utilizzo UML, ogni elemento del diagramma ha delle proprietà. Per visualizzare le proprietà di un elemento, fare clic con il pulsante destro del mouse sull'elemento nel diagramma o in **Esplora modelli UML** e quindi scegliere **Proprietà**. Le proprietà vengono visualizzate nella finestra **Proprietà** .

> [!NOTE]
> Questo argomento illustra le proprietà degli elementi nei diagrammi caso di utilizzo UML. Per altre informazioni su come leggere i diagrammi di attività UML, vedere [diagrammi caso di utilizzo UML:](../modeling/uml-use-case-diagrams-reference.md)informazioni di riferimento. Per altre informazioni su come creare diagrammi di attività UML, vedere [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Proprietà degli elementi

|proprietà|Impostazione predefinita|Elemento|Descrizione|
|--------------|-------------|-------------|-----------------|
|**Nome**|Nome predefinito|All|Identifica l'elemento.|
|**Nome completo**|Pacchetto :: Nome|All|Identifica l'elemento in modo univoco. Preceduto dal nome completo del pacchetto che lo contiene.|
|**Elementi di lavoro**|0 elementi associati|All|Numero di elementi di lavoro associati a questo elemento. Per associare elementi di lavoro, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|
|**Descrizione**|(nessuno)|All|Qui è possibile inserire note generali sull'elemento.|
|**Colore**|(predefinito)|All|Colore della forma. A differenza delle altre proprietà, non si tratta di una proprietà dell'elemento visualizzato dalla forma.|
|**Percorso immagine**|(nessuno)|Attore|Percorso del file di un'immagine da usare al posto dell'icona predefinita dell'attore. L'icona deve essere un file di risorse all'interno del progetto di Visual Studio.|
|**Soggetti**|(nessuno)|Caso di utilizzo|Sottosistema o un altro tipo proprietario del caso di utilizzo.<br /><br /> È possibile impostarlo posizionando il caso di utilizzo in un sottosistema del diagramma.|
|**Visibilità**|Public|Caso di utilizzo, attore, sottosistema|**Public** -visibile globalmente.<br /><br /> **Pacchetto** : visibile all'interno del pacchetto.|
|**IsAbstract**|False|Caso di utilizzo, attore, sottosistema|Se true, non è possibile creare un'istanza del tipo e rappresenta la base per la specializzazione tramite altre definizioni.|
|**Viene creata indirettamente**|True|Sottosistema|Il sottosistema esiste solo come elemento di progettazione. In fase di esecuzione esistono solo le relative parti.|
|**Collegamento ipertestuale**|(nessuno)|Elemento|URL o percorso di file del diagramma o del documento a cui l'elemento fornisce un collegamento.|

 Per un elenco delle proprietà delle associazioni, vedere [proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Vedere anche
 [Diagrammi caso d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md) [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)
