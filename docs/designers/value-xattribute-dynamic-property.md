---
title: Valore (proprietà dinamica XAttribute)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fefa3d13f1a38b5d1c329fa9df9220e13e769b1c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634525"
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
- [Proprietà dinamiche della classe XAttribute](../designers/value-xattribute-dynamic-property.md)
- [Attributo](../designers/attribute-xelement-dynamic-property.md)