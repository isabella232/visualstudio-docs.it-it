---
title: Xml (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87796afcc06190a54a3670581be7700fa8d49061
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940554"
---
# <a name="xml-xelement-dynamic-property"></a>XML (proprietà dinamica XElement)

Ottiene il contenuto XML non formattato dell'elemento.

## <a name="syntax"></a>Sintassi

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valore proprietà/valore restituito

Oggetto <xref:System.String> che rappresenta il contenuto XML non formattato dell'elemento.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> della classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con il parametro `SaveOptions` impostato su <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Vedere anche

- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valore](../designers/value-xelement-dynamic-property.md)