---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55157ab9a045b404175369e9682c525929f5e624
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460832"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Descrivono o specificano le proprietà di un processo.

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
Indica che il processo viene eseguito il debug da un debugger. Potrebbe essere un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger o potrebbe essere alcuni altri debugger, ad esempio, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica che il processo viene arrestato. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato. Disponibile in Visual Studio 2005 e versioni successive.

`PIFLAG_PROCESS_RUNNING`\
Indica che il processo è in esecuzione. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato. Disponibile in Visual Studio 2005 e versioni successive.

## <a name="remarks"></a>Note

Utilizzato per il `Flags` membro della [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura.

Questi flag possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)