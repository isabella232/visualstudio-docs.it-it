---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 405d11b0c685017d59251ba83126a73fe1a96db2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708966"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Specifica come interpretare un ID di processo nel [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="members"></a>Membri
ID del processo AD_PROCESS_ID_SYSTEM è un identificatore di sistema. Usare il `ProcessId.dwProcessId` campo le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura.

ID del processo AD_PROCESS_ID_GUID è un GUID. Usare la `ProcessId.guidProcessId` campo il `AD_PROCESS_ID` struttura.

## <a name="remarks"></a>Note
Utilizzato per il `ProcessIdType` membro del [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura per identificare il tipo di ID del processo che è contenuto nella struttura. Determina come interpretare il `ProcessId` union nella struttura.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
