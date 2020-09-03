---
title: Valore (proprietà dinamica XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664054"
---
# <a name="value-xattribute-dynamic-property"></a>Valore (proprietà dinamica XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ottiene o imposta il valore dell'attributo XML.

## <a name="syntax"></a>Sintassi

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito
 Oggetto <xref:System.String> contenente il valore dell'attributo.

## <a name="exceptions"></a>Eccezioni

|Tipo di eccezione|Condizione|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Durante l'impostazione, `value` è `null`.|

## <a name="remarks"></a>Osservazioni
 Questa proprietà dinamica è equivalente alla proprietà <xref:System.Xml.Linq.XAttribute.Value%2A> della classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ma supporta anche le notifiche delle modifiche.

## <a name="see-also"></a>Vedere anche
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[Attributo](../designers/attribute-xelement-dynamic-property.md) [proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)
