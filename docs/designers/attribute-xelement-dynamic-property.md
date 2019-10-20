---
title: Attributo (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d7fc1aa0419863e933bdc0a828455fcda8671fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637389"
---
# <a name="attribute-xelement-dynamic-property"></a>Attributo (proprietà dinamica XElement)

Ottiene un indicizzatore usato per recuperare l'istanza dell'attributo che corrisponde al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Indicizzatore del tipo `XAttribute Item(String expandedName)`. Questo indicizzatore accetta il nome espanso dell'attributo specificato e restituisce l'oggetto <xref:System.Xml.Linq.XAttribute> corrispondente o `null` se non esiste nessun attributo con il nome specificato.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XElement.Attribute%2A> della classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Proprietà dinamiche della classe XElement](../designers/attribute-xelement-dynamic-property.md)
- [Valore](../designers/value-xattribute-dynamic-property.md)