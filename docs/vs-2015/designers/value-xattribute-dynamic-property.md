---
title: Valore (proprietà dinamica XAttribute) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd9ea1fa163980a39bcd9981b9e1d757d72fcb6a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229151"
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
  
## <a name="remarks"></a>Note  
 Questa proprietà dinamica è equivalente alla proprietà <xref:System.Xml.Linq.XAttribute.Value%2A> della classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ma supporta anche le notifiche delle modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Proprietà dinamiche della classe XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Attributo](../designers/attribute-xelement-dynamic-property.md)



