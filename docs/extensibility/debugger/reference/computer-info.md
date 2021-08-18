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
ms.openlocfilehash: 461ff8398617b75e54460288e40f82bcdcf4e0b4660c51ca514b078a47d7ef22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452433"
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
