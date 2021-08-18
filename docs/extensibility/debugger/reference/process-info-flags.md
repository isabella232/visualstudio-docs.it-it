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
ms.openlocfilehash: c2708f2cdf4d2bb9150eaf1b5f235ddecc4164e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050533"
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
Indica che il processo è in fase di debug da parte di un debugger. Può trattarsi di un debugger o di un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] altro debugger, ad esempio WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica che il processo è stato arrestato. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene specificato anche . Disponibile in Visual Studio 2005 e versioni successive.

`PIFLAG_PROCESS_RUNNING`\
Indica che il processo è in esecuzione. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene specificato anche . Disponibile in Visual Studio 2005 e versioni successive.

## <a name="remarks"></a>Commenti

Usato per `Flags` il membro della [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura .

Questi flag possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
