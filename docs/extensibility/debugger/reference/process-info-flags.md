---
description: Descrive o specifica le proprietà di un processo.
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b1b72ade6d2cdc93ed3cb60ff5feba8589268f1b540692b5a9e8b3802ec31e89
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377301"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Descrive o specifica le proprietà di un processo.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
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
Indica che il debug del processo è in corso da parte di un debugger. Può trattarsi di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] un debugger o di un altro debugger, ad esempio WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica che il processo è stato arrestato. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene specificato anche . Disponibile in Visual Studio 2005 e versioni successive.

`PIFLAG_PROCESS_RUNNING`\
Indica che il processo è in esecuzione. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene specificato anche . Disponibile in Visual Studio 2005 e versioni successive.

## <a name="remarks"></a>Commenti

Utilizzato per `Flags` il membro della [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura .

Questi flag possono essere combinati con un bit per `OR` bit.

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
