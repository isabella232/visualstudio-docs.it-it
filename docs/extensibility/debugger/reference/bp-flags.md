---
title: proprietà BP_FLAGS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738066"
---
# <a name="bp_flags"></a>BP_FLAGS
Fornisce flag facoltativi che possono essere utilizzati per specificare informazioni aggiuntive durante l'impostazione di un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Campi
`BP_FLAG_NONE`\
Non specifica alcun flag del punto di interruzione.

`BP_FLAG_MAP_DOCPOSITION`\
Specifica che il motore di debug (DE) deve eseguire il mapping del punto di interruzione utilizzando la posizione del documento. Ciò è applicabile solo ai punti di interruzione impostati nei file di origine orientati agli script, ad esempio ASP (Active Server Pages).

`BP_FLAG_DONT_STOP`\
Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug non deve infine arrestarsi in tale posizione, ovvero non deve essere inviato un oggetto evento [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Questo flag è progettato per essere utilizzato principalmente con i punti di traccia.

## <a name="remarks"></a>Osservazioni
Utilizzato per `dwFlags` il membro delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
