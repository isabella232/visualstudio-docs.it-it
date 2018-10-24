---
title: Enumeratore di codice di stato directory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4ffdef238aaa628d0b72bcc945cf3dc1754fd8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833967"
---
# <a name="directory-status-code-enumerator"></a>Enumeratore di codice di stato directory
Il `SccDirStatus` enumeratore contiene denominati valori costanti che specificano lo stato di una directory nel sistema di controllo di origine. Questa enumerazione viene utilizzata per la [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Questa è stata introdotta nella versione 1.2 dell'API dei plug-in controllo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Membri  
 SCC_DIRSTATUS_INVALID  
 Non è stato possibile ottenere lo stato; non fare affidamento su di esso.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Directory non è incluso nel controllo del codice sorgente.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Directory è incluso nel controllo sorgente.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Progetto corrispondente a questa directory è vuota.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)