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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 368b18e7524e0cff31139de67f8092f9069246bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148050"
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
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valore](../designers/value-xelement-dynamic-property.md)
