---
title: Elemento (proprietà dinamica XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 520df74dae14fe672eb7d3db1bdc23a0a6437b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976758"
---
# <a name="element-xelement-dynamic-property"></a>Elemento (proprietà dinamica XElement)

Ottiene un indicizzatore usato per recuperare l'istanza dell'elemento figlio che corrisponde al nome espanso specificato.

## <a name="syntax"></a>Sintassi

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito

Indicizzatore del tipo `XElement Item(String expandedName)`. Questo indicizzatore accetta un parametro del nome espanso e restituisce l'oggetto <xref:System.Xml.Linq.XElement> corrispondente o `null` se non esiste nessun elemento con il nome specificato.

## <a name="remarks"></a>Note

Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Element%2A> della classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elementi](../designers/elements-xelement-dynamic-property.md)