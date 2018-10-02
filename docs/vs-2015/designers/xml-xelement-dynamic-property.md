---
title: Xml (proprietà dinamica XElement) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74fdfa59e791fb8e0262df04b1e45f3b867fbd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526261"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (proprietà dinamica XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Xml (proprietà dinamica XElement)](https://docs.microsoft.com/visualstudio/designers/xml-xelement-dynamic-property).  
  
Ottiene il contenuto XML non formattato dell'elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Oggetto <xref:System.String> che rappresenta il contenuto XML non formattato dell'elemento.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> della classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con il parametro `SaveOptions` impostato su <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valore](../designers/value-xelement-dynamic-property.md)



