---
description: Descrive il computer in cui è in esecuzione il debugger.
title: COMPUTER_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94e49ed1f72cd5477becc6a41abb10635d03805a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145653"
---
# <a name="computer_info"></a>COMPUTER_INFO
Descrive il computer in cui è in esecuzione il debugger.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>Members
`wProcessorArchitecture`\
Identifica l'architettura del microprocessore.

`wSuiteMask`\
Identifica la maschera della suite.

`dwOperatingSystemVersion`\
Numero di versione del sistema operativo.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita dal [metodo GetComputerInfo.](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
