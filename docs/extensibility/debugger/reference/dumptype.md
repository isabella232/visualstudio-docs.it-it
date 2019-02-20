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
ms.openlocfilehash: c81d9c9f3f5dc6b0a849e405133b7ecef1e4e59b
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412968"
---
# <a name="dumptype"></a>DUMPTYPE
Specifica la quantità di stato del programma (ad esempio thread in esecuzione, gli stack frame e indirizzo dell'istruzione corrente) per eseguire il dump.

## <a name="syntax"></a>Sintassi

```cpp
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

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
