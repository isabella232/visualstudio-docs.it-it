---
title: DUMPTYPE | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1548ca9205776e5a9677962bf620a350ede6c64e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525927"
---
# <a name="dumptype"></a>DUMPTYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DUMPTYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/dumptype).  
  
Specifica la quantità di stato del programma (ad esempio thread in esecuzione, gli stack frame e indirizzo dell'istruzione corrente) per eseguire il dump.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Membri  
 DUMP_MINIDUMP  
 Specifica un dump di piccole dimensioni e compatto.  
  
 DUMP_FULLDUMP  
 Specifica un dump completo e di grandi dimensioni.  
  
## <a name="remarks"></a>Note  
 Passato come argomento per il [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)

