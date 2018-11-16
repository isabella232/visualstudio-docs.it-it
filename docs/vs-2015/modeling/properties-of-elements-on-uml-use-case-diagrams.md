---
title: Diagrammi caso d'usano delle proprietà degli elementi su UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a81f7630a1a903af2f9c21aee3249ea6fe156af2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762817"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Proprietà di elementi in diagrammi caso d'uso UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma caso di utilizzo UML, ogni elemento del diagramma ha delle proprietà. Per visualizzare le proprietà di un elemento, fare doppio clic sull'elemento sul diagramma o nel **Esplora modelli UML** e quindi fare clic su **proprietà**. Le proprietà vengono visualizzate nel **proprietà** finestra.  
  
> [!NOTE]
>  Questo argomento illustra le proprietà degli elementi nei diagrammi caso di utilizzo UML. Per altre informazioni su come leggere i diagrammi attività UML, vedere [diagrammi caso d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md). Per altre informazioni su come creare diagrammi attività UML, vedere [diagrammi caso d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Proprietà degli elementi  
  
|Proprietà|Impostazione predefinita|Elemento|Descrizione|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nome predefinito|Tutti|Identifica l'elemento.|  
|**Nome completo**|Pacchetto :: Nome|Tutti|Identifica l'elemento in modo univoco. Preceduto dal nome completo del pacchetto che lo contiene.|  
|**Elementi di lavoro**|0 elementi associati|Tutti|Numero di elementi di lavoro associati a questo elemento. Per associare gli elementi di lavoro, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|  
|**Descrizione**|(nessuno)|Tutti|Qui è possibile inserire note generali sull'elemento.|  
|**Colore**|(predefinito)|Tutti|Colore della forma. A differenza delle altre proprietà, non si tratta di una proprietà dell'elemento visualizzato dalla forma.|  
|**Percorso dell'immagine**|(nessuno)|Attore|Percorso del file di un'immagine da usare al posto dell'icona predefinita dell'attore. L'icona deve essere un file di risorse all'interno del progetto di Visual Studio.|  
|**Argomenti**|(nessuno)|Caso di utilizzo|Sottosistema o un altro tipo proprietario del caso di utilizzo.<br /><br /> È possibile impostarlo posizionando il caso di utilizzo in un sottosistema del diagramma.|  
|**Visibilità**|Public|Caso di utilizzo, attore, sottosistema|**Pubblica** : visibile globalmente.<br /><br /> **Pacchetto** : visibile all'interno del pacchetto.|  
|**IsAbstract**|False|Caso di utilizzo, attore, sottosistema|Se true, non è possibile creare un'istanza del tipo e rappresenta la base per la specializzazione tramite altre definizioni.|  
|**Is Indirectly Instantiated**|True|Sottosistema|Il sottosistema esiste solo come elemento di progettazione. In fase di esecuzione esistono solo le relative parti.|  
|**Collegamento ipertestuale**|(nessuno)|Elemento|URL o percorso di file del diagramma o del documento a cui l'elemento fornisce un collegamento.|  
  
 Per un elenco delle proprietà di associazioni, vedere [proprietà delle associazioni nei UML diagrammi classi](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi caso di utilizzo UML: riferimento](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammi casi d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md)



