---
description: Descrive una matrice di identificatori univoci per i motori di debug disponibili.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0dc91c33672519a7bed0bc545179d91915ab38d1142728c2c614f6924548c411
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434269"
---
# <a name="guid_array"></a>GUID_ARRAY
Descrive una matrice di identificatori univoci per i motori di debug disponibili.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Members
`dwCount`\
Numero di identificatori univoci nella matrice.

`Members`\
Matrice contenente identificatori univoci.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita dal [metodo GetEngineFilter.](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
