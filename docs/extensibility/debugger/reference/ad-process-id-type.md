---
description: Specifica come interpretare un ID processo nella struttura AD_PROCESS_ID processo.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9fad5d6bb577864b60c7916ac51b4cf84790cf3235e044717fd58a31c7dabd22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434503"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Specifica come interpretare un ID processo nella struttura AD_PROCESS_ID [processo.](../../../extensibility/debugger/reference/ad-process-id.md)

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
L'ID processo è un identificatore di sistema. Usare il `ProcessId.dwProcessId` campo della [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura.

`AD_PROCESS_ID_GUID`\
L'ID processo è un GUID. Usare il `ProcessId.guidProcessId` campo della `AD_PROCESS_ID` struttura .

## <a name="remarks"></a>Commenti
Usato per il membro della struttura AD_PROCESS_ID per identificare il tipo di `ProcessIdType` ID processo contenuto nella struttura . [](../../../extensibility/debugger/reference/ad-process-id.md) Determina come interpretare `ProcessId` l'unione nella struttura .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
