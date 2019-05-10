---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f3485aa2e5650345c0b14c6cb8093034043285a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461005"
---
# <a name="messagetype"></a>MESSAGETYPE
Specifica il tipo di messaggio e il motivo.

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
 Indica che deve essere inviato il messaggio nella finestra di output. Ciò si escludono a vicenda da `MT_MESSAGEBOX`.

 `MT_MESSAGEBOX`\
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Ciò si escludono a vicenda da `MT_OUTPUTSTRING`.

 `MT_TYPE_MASK`\
 Un valore della maschera per isolare la destinazione del messaggio.

 `MT_REASON_EXCEPTION`\
 Indica che è attualmente visualizzata una finestra di messaggio come risultato un'eccezione. Ciò si escludono a vicenda da `MT_REASON_TRACEPOINT`.

 `MT_REASON_TRACEPOINT`\
 Indica che una finestra di messaggio viene visualizzata in seguito a raggiungere un punto di analisi. Ciò si escludono a vicenda per `MT_REASON_EXCEPTION`.

 `MT_REASON_MASK`\
 Un valore della maschera per isolare il motivo per il messaggio da visualizzare.

## <a name="remarks"></a>Note
 Questi valori vengono restituiti dai [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metodi.

 Uno dei valori di motivo può essere combinato con uno dei valori di destinazione di output con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)