---
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab7d66ecae911faf8cc42a840ac853d585fc80bb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012576"
---
# <a name="dumptype"></a>DUMPTYPE
Specifica la quantità di stato del programma (ad esempio thread in esecuzione, gli stack frame e indirizzo dell'istruzione corrente) per eseguire il dump.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
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
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)