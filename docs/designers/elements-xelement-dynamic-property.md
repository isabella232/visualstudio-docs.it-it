---
title: Elementi (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c78dece049aa2d446a0f03b24f3e2c2640131327
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924411"
---
# <a name="elements-xelement-dynamic-property"></a>Elementi (proprietà dinamica XElement)

Ottiene un indicizzatore usato per recuperare gli elementi figlio dell'elemento corrente che corrispondono al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Indicizzatore del tipo `IEnumerable<XElement> Item(String expandedName)`. Questo indicizzatore assume il nome espanso degli elementi figlio desiderati e restituisce gli elementi figlio corrispondenti in una raccolta <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> della classe <xref:System.Xml.Linq.XContainer>.

Gli elementi della raccolta restituita sono in ordine del documento dell'origine XML.

Questa proprietà usa l'esecuzione posticipata.

## <a name="see-also"></a>Vedere anche

- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elemento](../designers/element-xelement-dynamic-property.md)
- [Discendenti](../designers/descendants-xelement-dynamic-property.md)