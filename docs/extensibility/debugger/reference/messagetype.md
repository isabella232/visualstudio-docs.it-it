---
description: Specifica il tipo e il motivo del messaggio.
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd7b10217313be30dd795a8ff108c3c30e214490
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222432"
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
 Indica che il messaggio deve essere inviato alla finestra di output. Si escludono a vicenda `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Si escludono a vicenda `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Valore della maschera per isolare la destinazione del messaggio.

 `MT_REASON_EXCEPTION`\
 Indica che una finestra di messaggio viene visualizzata come risultato di un'eccezione. Si escludono a vicenda `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Indica che una finestra di messaggio viene visualizzata come risultato dell'esecuzione di un punto di analisi. Si escludono a vicenda `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Valore della maschera per isolare il motivo del messaggio visualizzato.

## <a name="remarks"></a>Commenti
 Questi valori vengono restituiti dai metodi [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .

 Uno dei motivi per cui i valori possono essere combinati con uno dei valori di destinazione di output utilizzando un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
