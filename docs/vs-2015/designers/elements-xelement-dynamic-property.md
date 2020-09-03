---
title: Elementi (proprietà dinamica XElement)) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664686"
---
# <a name="elements-xelement-dynamic-property"></a>Elementi (proprietà dinamica XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ottiene un indicizzatore usato per recuperare gli elementi figlio dell'elemento corrente che corrispondono al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito
 Indicizzatore del tipo `IEnumerable<XElement> Item(String expandedName)`. Questo indicizzatore assume il nome espanso degli elementi figlio desiderati e restituisce gli elementi figlio corrispondenti in una raccolta <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Osservazioni
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> della classe <xref:System.Xml.Linq.XContainer>.

 Gli elementi della raccolta restituita sono in ordine del documento dell'origine XML.

 Questa proprietà usa l'esecuzione posticipata.

## <a name="see-also"></a>Vedere anche
 [Discendenti](../designers/descendants-xelement-dynamic-property.md) dell' [elemento](../designers/element-xelement-dynamic-property.md) [proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
