---
title: Aggiungere stringhe di riferimento a elementi del modello UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672796"
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
 [Definire un gestore dei collegamenti agli elementi di lavoro](../modeling/define-a-work-item-link-handler.md) [definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md) [programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)
