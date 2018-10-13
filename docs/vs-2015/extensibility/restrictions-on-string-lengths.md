---
title: Limitazioni sulle lunghezze di stringa | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f600ef47526c3b2d9e703781c8f20ddb563dcf4a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206228"
---
# <a name="restrictions-on-string-lengths"></a>Limitazioni delle lunghezze di stringa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'API dei plug-in del controllo origine limita la lunghezza delle stringhe usate nelle varie funzioni.  
  
## <a name="string-length-values"></a>Valori di lunghezza stringa  
  
|Costante|Valore|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  La lunghezza non include la terminazione `null`. Altre costanti con suffisso "dimen_sione" anziché "_LEN" include lo spazio per la terminazione `null`.  
  
|Costante|Valore|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)

