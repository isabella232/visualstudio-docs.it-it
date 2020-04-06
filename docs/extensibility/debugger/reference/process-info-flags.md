---
title: proprietà PROCESS_INFO_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713957"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Descrive o specifica le proprietà di un processo.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Campi

`PIFLAG_SYSTEM_PROCESS`\
Indica che il processo è un processo di sistema.

`PIFLAG_DEBUGGER_ATTACHED`\
Indica che il processo viene sottoposto a debug da un debugger. Può essere [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] un debugger o può essere un altro debugger, ad esempio WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica che il processo è stato arrestato. Valido solo `PIFLAG_DEBUGGER_ATTACHED` se specificato. Disponibile in Visual Studio 2005 e versioni successive.

`PIFLAG_PROCESS_RUNNING`\
Indica che il processo è in esecuzione. Valido solo `PIFLAG_DEBUGGER_ATTACHED` se specificato. Disponibile in Visual Studio 2005 e versioni successive.

## <a name="remarks"></a>Osservazioni

Utilizzato per `Flags` il membro della [struttura PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
