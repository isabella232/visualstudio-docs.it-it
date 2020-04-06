---
title: proprietà AD_PROCESS_ID_TYPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738197"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Specifica come interpretare un ID di processo nella struttura [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

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
ID processo è un identificatore di sistema. Utilizzare `ProcessId.dwProcessId` il campo della struttura [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

`AD_PROCESS_ID_GUID`\
ID processo è un GUID. Utilizzare `ProcessId.guidProcessId` il campo `AD_PROCESS_ID` della struttura.

## <a name="remarks"></a>Osservazioni
Utilizzato per `ProcessIdType` il membro della [struttura AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) per identificare il tipo di ID processo contenuto nella struttura. Determina come interpretare l'unione `ProcessId` nella struttura.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
