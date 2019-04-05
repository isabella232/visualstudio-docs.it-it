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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966768"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica il tipo di messaggio e il motivo.  
  
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
 Indica che deve essere inviato il messaggio nella finestra di output. Ciò si escludono a vicenda da `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indica che il messaggio deve essere visualizzato in una finestra di messaggio. Ciò si escludono a vicenda da `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Un valore della maschera per isolare la destinazione del messaggio.  
  
 MT_REASON_EXCEPTION  
 Indica che è attualmente visualizzata una finestra di messaggio come risultato un'eccezione. Ciò si escludono a vicenda da `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indica che una finestra di messaggio viene visualizzata in seguito a raggiungere un punto di analisi. Ciò si escludono a vicenda per `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Un valore della maschera per isolare il motivo per il messaggio da visualizzare.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono restituiti dai [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metodi.  
  
 Uno dei valori di motivo può essere combinato con uno dei valori di destinazione di output con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
