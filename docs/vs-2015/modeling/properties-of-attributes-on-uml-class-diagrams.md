---
title: Proprietà degli attributi nei diagrammi classi UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652072"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Proprietà di attributi in diagrammi classi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma classi UML è possibile aggiungere *attributi* a classi e interfacce. Un attributo definisce i valori che possono essere associati a istanze della classe o dell'interfaccia.

 Per aggiungere un attributo, fare clic con il pulsante destro del mouse sulla classe o sull'interfaccia, scegliere **Aggiungi**e quindi fare clic su **Attributo**.

 Se gli attributi di una classe nel diagramma non sono visibili, fare clic sulla freccia di espansione nella parte superiore della classe o dell'interfaccia. Se l'intestazione **Attributi** è visibile, fare clic sul simbolo **[+]** per espandere la sezione degli attributi.

## <a name="signature-of-an-attribute"></a>Firma di un attributo
 La firma di un attributo è la riga che lo rappresenta in una classe o in un'interfaccia di un diagramma classi UML. Il formato è il seguente:

```
+ AttributeName : TypeName [*]
```

 \+ indica la visibilità pubblica. Gli altri valori consentiti sono: (private), # (protected), ~ (package).

 `AttributeName` è sottolineato se l'attributo è statico.

 `: TypeName` viene omesso se l'attributo non dispone di alcun tipo.

 `[*]` indica la molteplicità. Viene omesso se la molteplicità è 1.

## <a name="properties"></a>Proprietà
 La tabella seguente descrive le proprietà di un attributo in una classe o in un'interfaccia in un diagramma classi UML.

 Per visualizzare le proprietà di un attributo, fare clic con il pulsante destro del mouse sull'attributo nella classe o nell'interfaccia del diagramma e quindi scegliere **Proprietà**. Le proprietà vengono visualizzate nella finestra Proprietà.

 Per visualizzare le proprietà di un attributo, fare clic con il pulsante destro del mouse sull'attributo e quindi scegliere **Proprietà**.

|   **Proprietà**    | **Default**  |                                                                                                                                                                                                         Descrizione                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valore predefinito** |   (vuoto)    |                                                                                                                                                                               Valore dell'attributo quando viene creata un'istanza del classificatore.                                                                                                                                                                                |
| **Is Read Only**  |    Falso     |                                                                                                                                                                                    Se true, il valore dell'attributo non può essere modificato.                                                                                                                                                                                    |
|   **Is Static**   |    Falso     |                                                                                                                    Se true, un singolo valore per questo attributo viene condiviso tra tutte le istanze di questo tipo.<br /><br /> Se true, il nome dell'attributo è sottolineato laddove viene visualizzato nel diagramma.                                                                                                                    |
|     **Name**      | (nuovo nome) |                                                                                                                                                                                        Deve essere univoco all'interno del classificatore proprietario.                                                                                                                                                                                        |
|     **Tipo**      |    (nessuna)    |                                                Un tipo primitivo come **Integer**o un tipo definito nel modello. Non è possibile usare tipi non primitivi, ad esempio **Decimal** , perché il valore deve essere codificato nei metadati. Se si immette un nome per un nuovo tipo di questa proprietà, verrà aggiunto un tipo nella sezione **Tipi non specificati** di Esplora modelli UML.                                                 |
|  **Visibilità**   |    Pubblico    |                                     I valori consentiti e i caratteri visualizzati nella firma sono:<br /><br /> **+ Public** : visibile a livello globale<br /><br /> **- Private** : non visibile all'esterno del tipo proprietario<br /><br /> **# Protected** : visibile ai tipi derivati dal proprietario<br /><br /> **~ Package** : visibile agli altri tipi all'interno dello stesso pacchetto.                                      |
|  **Elementi di lavoro**   | 0 elementi associati |                                                                                                                          Numero di elementi di lavoro associati. Sola lettura.<br /><br /> Per altre informazioni, vedere [collegare elementi del modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Is Leaf**    |    Falso     |                                                                                                                                                                    Se true, non è destinato a consentire la ridefinizione di questo attributo nei tipi derivati.                                                                                                                                                                     |
|  **Is Derived**   |    Falso     |                                                                                                              Se true, questo attributo viene calcolato da altri attributi. Ad esempio, Diagonale viene calcolato sulla base di Larghezza e Altezza. I dettagli devono essere scritti in **Descrizione** o in un commento allegato.                                                                                                              |
|  **Descrizione**  |   (vuoto)    |                                                                                                                                                                        Per le note generali o per la definizione dei vincoli sui valori nell'attributo.                                                                                                                                                                        |
| **Molteplicità**  |      1       | **1** : questo attributo ha un singolo valore del tipo specificato.<br /><br /> **0..1** : questo attributo può avere un valore pari a `null`.<br /><br /> **\\**\* : il valore di questo attributo è una raccolta di valori.<br /><br /> **1.. \\ .** \* il valore di questo attributo è una raccolta che contiene almeno un valore.<br /><br /> *n* **..** *m* : il valore di questo attributo è una raccolta che contiene valori compresi tra *n* e *m* . |
|  **Is Ordered**   |    Falso     |                                                                                                                                                                    Se true, la raccolta forma un elenco sequenziale. Per **Multiplicity** maggiore di 1.                                                                                                                                                                     |
|   **Univoco**   |    Falso     |                                                                                                                                                                Se true, non sono presenti valori duplicati nella raccolta. Per **Multiplicity** maggiore di 1.                                                                                                                                                                |

## <a name="see-also"></a>Vedere anche
 [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md) [proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [proprietà di operazioni in diagrammi](../modeling/properties-of-operations-on-uml-class-diagrams.md) classi UML [diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md) [diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)
