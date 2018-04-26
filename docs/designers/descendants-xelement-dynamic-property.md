---
title: Discendenti (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1b0aa0c55c0da2a6f9af58f5d54ff607a409ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="descendants-xelement-dynamic-property"></a>Discendenti (proprietà dinamica XElement)

Ottiene un indicizzatore usato per recuperare tutti gli elementi discendente dell'elemento corrente che corrispondono al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Indicizzatore del tipo `IEnumerable<XElement> Item(String expandedName)`. Questo indicizzatore accetta il nome espanso degli elementi discendente specificati e restituisce gli elementi figlio corrispondenti in una raccolta <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> della classe <xref:System.Xml.Linq.XContainer>.

Gli elementi della raccolta restituita sono in ordine del documento dell'origine XML.

Questa proprietà usa l'esecuzione posticipata.

## <a name="see-also"></a>Vedere anche

- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elementi](../designers/elements-xelement-dynamic-property.md)