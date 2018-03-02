---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6e95e9f66b804fed102c0d51aa17a1bfe4f51ca5
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Viene descritta o specifica le proprietà di un processo.

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

## <a name="members"></a>Membri

PIFLAG_SYSTEM_PROCESS  
Indica che il processo è un processo di sistema.

PIFLAG_DEBUGGER_ATTACHED  
Indica che il processo viene eseguito il debug da un debugger. Potrebbe essere un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger, oppure può essere di alcuni altri debugger, ad esempio, WinDbg.

PIFLAG_PROCESS_STOPPED  
Indica che il processo viene arrestato. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato. Disponibile in Visual Studio 2005 e versioni successive.

PIFLAG_PROCESS_RUNNING  
Indica che il processo è in esecuzione. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato. Disponibile in Visual Studio 2005 e versioni successive.

## <a name="remarks"></a>Note

Utilizzato per il `Flags` appartenente il [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura.

Questi flag possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)