---
title: Elementi (proprietà dinamica XElement)) | Microsoft Docs
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
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75cb7f8f6a5259151679ecee84bbeb5db336782f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519903"
---
# <a name="elements-xelement-dynamic-property"></a>Elementi (proprietà dinamica XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elementi (proprietà dinamica XElement)](https://docs.microsoft.com/visualstudio/designers/elements-xelement-dynamic-property).  
  
Ottiene un indicizzatore usato per recuperare gli elementi figlio dell'elemento corrente che corrispondono al nome espanso specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Indicizzatore del tipo `IEnumerable<XElement> Item(String expandedName)`. Questo indicizzatore assume il nome espanso degli elementi figlio desiderati e restituisce gli elementi figlio corrispondenti in una raccolta <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è equivalente al metodo <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> della classe <xref:System.Xml.Linq.XContainer>.  
  
 Gli elementi della raccolta restituita sono in ordine del documento dell'origine XML.  
  
 Questa proprietà usa l'esecuzione posticipata.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà dinamiche della classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elemento](../designers/element-xelement-dynamic-property.md)   
 [Discendenti](../designers/descendants-xelement-dynamic-property.md)



