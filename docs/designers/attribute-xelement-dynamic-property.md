---
title: Attributo (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926923"
---
# <a name="attribute-xelement-dynamic-property"></a>Attributo (proprietà dinamica XElement)

Ottiene un indicizzatore usato per recuperare l'istanza dell'attributo che corrisponde al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Indicizzatore del tipo `XAttribute Item(String expandedName)`. Questo indicizzatore accetta il nome espanso dell'attributo specificato e restituisce l'oggetto <xref:System.Xml.Linq.XAttribute> corrispondente o `null` se non esiste nessun attributo con il nome specificato.

## <a name="remarks"></a>Osservazioni

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XElement.Attribute%2A> della classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valore](../designers/value-xattribute-dynamic-property.md)