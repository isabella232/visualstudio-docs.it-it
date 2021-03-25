---
description: Specifica come interpretare un ID di processo nella struttura AD_PROCESS_ID.
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ae50fc827debd540faa99c33e10ddd217fc691f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094562"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Specifica come interpretare un ID di processo nella struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

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

## <a name="fields"></a>Campi
`AD_PROCESS_ID_SYSTEM`\
ID processo è un identificatore di sistema. Utilizzare il `ProcessId.dwProcessId` campo della struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

`AD_PROCESS_ID_GUID`\
ID processo è un GUID. Utilizzare il `ProcessId.guidProcessId` campo della `AD_PROCESS_ID` struttura.

## <a name="remarks"></a>Commenti
Utilizzato per il `ProcessIdType` membro della struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) per identificare il tipo di ID processo contenuto nella struttura. Determina come interpretare l' `ProcessId` Unione nella struttura.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
