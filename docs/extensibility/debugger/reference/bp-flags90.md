---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e81a384686303ecba2225dfcc865ae7f390664b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025302"
---
# <a name="bpflags90"></a>BP_FLAGS90
Enumera i valori validi per i flag facoltativi. Il flag facoltativo consente di specificare informazioni aggiuntive quando si imposta un punto di interruzione. Questa enumerazione estende la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumerazione.  
  
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
  
#### <a name="parameters"></a>Parametri  
 BP90_FLAG_NONE  
 Non specifica alcun flag per il punto di interruzione.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Specifica che il motore di debug (DE) deve eseguire il mapping del punto di interruzione usando la posizione del documento. Ciò si applica solo ai punti di interruzione impostati nei file di origine orientata ai servizi script, ad esempio le pagine ASP (Active Server).  
  
 BP90_FLAG_DONT_STOP  
 Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug in definitiva non deve arrestare vale a dire, un' [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) oggetto dell'evento non deve essere inviato. Questo flag è progettato per essere utilizzati principalmente con i punti di traccia.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Utilizzato dal motore di debug nativo per determinare se lo stato di avanzamento nell'esecuzione deve essere cancellato. Si differenzia dal BP90_FLAG_DONT_STOP perché BP90_FLAG_DONT_STOP non è impostato se il punto di traccia viene eseguita una macro.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg90.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)