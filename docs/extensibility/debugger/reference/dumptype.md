---
description: Specifica la quantità di stato di un programma (ad esempio thread in esecuzione, stack frame e indirizzo di istruzione corrente) di cui eseguire il dump.
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3054d86c1d516f79cbf259eaaf4add7ae1befc51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104625"
---
# <a name="dumptype"></a>DUMPTYPE
Specifica la quantità di stato di un programma (ad esempio thread in esecuzione, stack frame e indirizzo di istruzione corrente) di cui eseguire il dump.

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

## <a name="fields"></a>Campi
`DUMP_MINIDUMP`\
Specifica un dump compatto di piccole dimensioni.

`DUMP_FULLDUMP`\
Specifica un dump completo di grandi dimensioni.

## <a name="remarks"></a>Commenti
Passato come argomento al [metodo WriteDump.](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
