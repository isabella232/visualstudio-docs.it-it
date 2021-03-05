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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f56ca1db0462a85bd68b193147f5dd3a46c6bee9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164344"
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
