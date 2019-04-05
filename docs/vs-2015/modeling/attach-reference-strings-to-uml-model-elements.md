---
title: Allegare stringhe di riferimento agli elementi del modello UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd5a1ae4abc2e0b5c508b7b77160bbf8da3bb45e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964558"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Allegare stringhe di riferimento agli elementi del modello UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile scrivere codice per allegare stringhe arbitrarie agli elementi del modello. Una stringa può essere, ad esempio, un URI, il risultato memorizzato nella cache di un calcolo o un riferimento del bus di modelli a un elemento in un altro modello. Ogni stringa è contenuta in un oggetto IReference. A ogni elemento del modello è possibile allegare il un numero di oggetti IReference desiderato.  
  
 A ogni oggetto IReference è associato un nome. Questo nome può essere usato per indicare come deve essere interpretato il valore di riferimento. Ad esempio, è possibile impostare il nome su "URI" per indicare che il valore deve essere interpretato come un URI. Sono disponibili alcuni valori di nomi di riferimento predefiniti usati dagli strumenti di modellazione.  
  
## <a name="attaching-a-reference-to-an-ielement"></a>Associazione di un riferimento a un oggetto IElement  
 Per usare i metodi seguenti, è necessario aggiungere un riferimento a:  
  
 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
 È necessario inserire questa direttiva nel codice:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
|Chiamata al metodo|Descrizione|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Crea un oggetto `IReference` con le stringhe di nome e valore specificate e lo collega a `element`. Restituisce `IReference`.<br /><br /> Genera un'eccezione se `duplicatesAllowed` è false ed è già presente un oggetto `IReference` con lo stesso nome associato a `element`.|  
|`element.GetReferences(name)`|Restituisce gli oggetti `IReference` collegati a `element` con l'oggetto `name` specificato.|  
|`element.DeleteAllReferences(name)`|Elimina tutti gli oggetti `IReference` collegati all'elemento con il nome specificato.|  
|`reference.Delete()`|Elimina questo oggetto `IReference`.|  
|`ReferenceConstants.WorkItem`|Valore usato per denominare i riferimenti agli elementi di lavoro.|  
  
## <a name="see-also"></a>Vedere anche  
 [Definire un gestore di collegamento elemento di lavoro](../modeling/define-a-work-item-link-handler.md)   
 [Definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md)   
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)
