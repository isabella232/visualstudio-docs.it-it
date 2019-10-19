---
title: Xml (proprietà dinamica XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663840"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (proprietà dinamica XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ottiene il contenuto XML non formattato dell'elemento.

## <a name="syntax"></a>Sintassi

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito
 Oggetto <xref:System.String> che rappresenta il contenuto XML non formattato dell'elemento.

## <a name="remarks"></a>Osservazioni
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> della classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con il parametro `SaveOptions` impostato su <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Vedere anche
 [Valore](../designers/value-xelement-dynamic-property.md) delle [proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)
