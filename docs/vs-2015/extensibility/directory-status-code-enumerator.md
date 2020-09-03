---
title: Enumeratore del codice di stato della directory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185249"
---
# <a name="directory-status-code-enumerator"></a>Enumeratore di codice di stato directory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' `SccDirStatus` enumeratore contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo del codice sorgente. Questa enumerazione viene utilizzata da [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Questa operazione è stata introdotta nella versione 1,2 dell'API del plug-in del controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Membri  
 SCC_DIRSTATUS_INVALID  
 Non è stato possibile ottenere lo stato; non fare affidamento su di esso.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 La directory non è sotto il controllo del codice sorgente.  
  
 SCC_DIRSTATUS_CONTROLLED  
 La directory è sotto il controllo del codice sorgente.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Il progetto corrispondente a questa directory è vuoto.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
