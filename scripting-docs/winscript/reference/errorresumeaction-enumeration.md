---
title: Enumerazione ERRORRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d78852a05226f5112447dd142c06a2ba55ddba5a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347229"
---
# <a name="errorresumeaction-enumeration"></a>Enumerazione ERRORRESUMEACTION
Descrive come proseguire a seguito di un errore di runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Esegue nuovamente l'istruzione che ha generato l'errore.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Consente il motore del linguaggio di gestire l'errore.|  
|ERRORRESUMEACTION_SkipErrorStatement|Riprende l'esecuzione di codice che segue l'istruzione che ha generato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)