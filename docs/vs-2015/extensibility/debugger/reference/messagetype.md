---
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547208"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica il tipo e il motivo del messaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
## <a name="members"></a>Membri  
 MT_OUTPUTSTRING  
 Indica che il messaggio deve essere inviato alla finestra di output. Si escludono a vicenda `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Si escludono a vicenda `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 Valore della maschera per isolare la destinazione del messaggio.  
  
 MT_REASON_EXCEPTION  
 Indica che una finestra di messaggio viene visualizzata come risultato di un'eccezione. Si escludono a vicenda `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 Indica che una finestra di messaggio viene visualizzata come risultato dell'esecuzione di un punto di analisi. Si escludono a vicenda `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 Valore della maschera per isolare il motivo del messaggio visualizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Questi valori vengono restituiti dai metodi [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 Uno dei motivi per cui i valori possono essere combinati con uno dei valori di destinazione di output utilizzando un bit per bit `OR` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
