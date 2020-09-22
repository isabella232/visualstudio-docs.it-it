---
title: Restrizioni sulle lunghezze di stringa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc6ff1e77a9a973e184384d98ef8b880aaa2f005
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839507"
---
# <a name="restrictions-on-string-lengths"></a>Limitazioni delle lunghezze di stringa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'API del plug-in del controllo del codice sorgente limita le lunghezze delle stringhe utilizzate in diverse funzioni.  
  
## <a name="string-length-values"></a>Valori di lunghezza stringa  
  
|Costante|valore|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
> La lunghezza non include la terminazione `null` . Altre costanti con suffisso "_SIZE" invece di "_LEN" includono spazio per la terminazione `null` .  
  
|Costante|valore|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
