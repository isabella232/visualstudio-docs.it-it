---
description: Fornisce flag facoltativi che possono essere utilizzati per specificare informazioni aggiuntive quando si imposta un punto di interruzione.
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f0d79bd6e3c1495f85ed6f8436a781445173810
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104651"
---
# <a name="bp_flags"></a>BP_FLAGS
Fornisce flag facoltativi che possono essere utilizzati per specificare informazioni aggiuntive quando si imposta un punto di interruzione.

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
Specifica che il motore di debug deve eseguire il mapping del punto di interruzione usando la posizione del documento. Questa opzione è applicabile solo ai punti di interruzione impostati nei file di origine orientati agli script, ad esempio Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che in definitiva il motore di debug non deve arrestarsi in questo punto, ovvero non deve essere inviato un oggetto evento [IDebugBreakpointEvent2.](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Questo flag è progettato per essere usato principalmente con punti di traccia.

## <a name="remarks"></a>Commenti
Usato per `dwFlags` il membro delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
