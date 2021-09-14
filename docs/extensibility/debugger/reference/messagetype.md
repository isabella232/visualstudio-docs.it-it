---
description: Specifica il tipo e il motivo del messaggio.
title: MessageTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3172188d878d40d3957ea56ff3c6f57ca561a1be
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634795"
---
# <a name="messagetype"></a>MESSAGETYPE
Specifica il tipo e il motivo del messaggio.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MESSAGETYPE { 
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
public enum enum_MESSAGETYPE { 
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
 Indica che il messaggio deve essere inviato alla finestra di output. Si escludono a vicenda da `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Si escludono a vicenda da `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Valore della maschera per isolare la destinazione del messaggio.

 `MT_REASON_EXCEPTION`\
 Indica che una finestra di messaggio viene visualizzata come risultato di un'eccezione. Si escludono a vicenda da `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Indica che una finestra di messaggio viene visualizzata come risultato del clic su un punto di traccia. Si escludono a vicenda con `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Valore della maschera per isolare il motivo del messaggio visualizzato.

## <a name="remarks"></a>Commenti
 Questi valori vengono restituiti dai [metodi GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) [e GetErrorMessage.](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

 Uno dei valori di motivo può essere combinato con uno dei valori di destinazione di output usando un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
