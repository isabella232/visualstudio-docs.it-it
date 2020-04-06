---
title: PROPRIETÀ MESSAGETYPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714490"
---
# <a name="messagetype"></a>MESSAGETYPE
Specifica il tipo e il motivo del messaggio.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Campi
 `MT_OUTPUTSTRING`\
 Indica che il messaggio deve essere inviato alla finestra di output. Questo si escludono a vicenda da `MT_MESSAGEBOX`.

 `MT_MESSAGEBOX`\
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Questo si escludono a vicenda da `MT_OUTPUTSTRING`.

 `MT_TYPE_MASK`\
 Valore maschera per isolare la destinazione del messaggio.

 `MT_REASON_EXCEPTION`\
 Indica che una finestra di messaggio viene visualizzata come risultato di un'eccezione. Questo si escludono a vicenda da `MT_REASON_TRACEPOINT`.

 `MT_REASON_TRACEPOINT`\
 Indica che viene visualizzata una finestra di messaggio come risultato di un punto di analisi. Questo si escludono a vicenda per `MT_REASON_EXCEPTION`.

 `MT_REASON_MASK`\
 Valore della maschera per isolare il motivo della visualizzazione del messaggio.

## <a name="remarks"></a>Osservazioni
 Questi valori vengono restituiti dal [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metodi.

 Uno dei valori di motivo può essere combinato con `OR`uno dei valori di destinazione dell'output utilizzando un oggetto bit per bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
