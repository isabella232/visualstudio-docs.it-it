---
title: Valore (proprietà dinamica XAttribute)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe9127d4a7c691c34f15d399bd32f5e48cc6f0ed
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908543"
---
# <a name="value-xattribute-dynamic-property"></a>Valore (proprietà dinamica XAttribute)

Ottiene o imposta il valore dell'attributo XML.

## <a name="syntax"></a>Sintassi

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito

Oggetto <xref:System.String> contenente il valore dell'attributo.

## <a name="exceptions"></a>Eccezioni

|Tipo di eccezione|Condizione|
| - |---------------|
|<xref:System.ArgumentNullException>|Durante l'impostazione, `value` è `null`.|

## <a name="remarks"></a>Note

Questa proprietà dinamica è equivalente alla proprietà <xref:System.Xml.Linq.XAttribute.Value%2A> della classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ma supporta anche le notifiche delle modifiche.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Attributo](../designers/attribute-xelement-dynamic-property.md)