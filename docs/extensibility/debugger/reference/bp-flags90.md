---
description: Enumera i valori validi per i flag facoltativi.
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24e6b8bcefd47ddded83c28fc7d5df71327ced86
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080104"
---
# <a name="bp_flags90"></a>BP_FLAGS90
Enumera i valori validi per i flag facoltativi. I flag facoltativi possono essere usati per specificare informazioni aggiuntive quando si imposta un punto di interruzione. Questa enumerazione estende [l'BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) di dati.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>Campi
`BP90_FLAG_NONE`\
Non specifica alcun flag del punto di interruzione.

`BP90_FLAG_MAP_DOCPOSITION`\
Specifica che il motore di debug deve eseguire il mapping del punto di interruzione usando la posizione del documento. Ciò è applicabile solo ai punti di interruzione impostati nei file di origine orientati agli script, ad esempio Active Server Pages (ASP).

`BP90_FLAG_DONT_STOP`\
Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug in ultima analisi non deve arrestarsi. ciò significa che un oggetto evento [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) non deve essere inviato. Questo flag è progettato per essere usato principalmente con punti di traccia.

`BP90_FLAG_TRACEPOINT_CONTINUE`\
Utilizzato dal motore di debug nativo per determinare se lo stato di esecuzione del passaggio deve essere cancellato. È diverso da BP90_FLAG_DONT_STOP perché BP90_FLAG_DONT_STOP non è impostato se il punto di traccia esegue una macro.

## <a name="requirements"></a>Requisiti
Intestazione: Msdbg90.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
