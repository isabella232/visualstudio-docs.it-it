---
title: Elemento (proprietà dinamica XElement) | Microsoft Docs
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
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56689506db04ee2aedd484093506db4a4fc7453d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529993"
---
# <a name="element-xelement-dynamic-property"></a>Elemento (proprietà dinamica XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento (proprietà dinamica XElement)](https://docs.microsoft.com/visualstudio/designers/element-xelement-dynamic-property).  
  
Ottiene un indicizzatore usato per recuperare l'istanza dell'elemento figlio che corrisponde al nome espanso specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Indicizzatore del tipo `XElement Item(String expandedName)`. Questo indicizzatore accetta un parametro del nome espanso e restituisce l'oggetto <xref:System.Xml.Linq.XElement> corrispondente o `null` se non esiste nessun elemento con il nome specificato.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Element%2A> della classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementi](../designers/elements-xelement-dynamic-property.md)



