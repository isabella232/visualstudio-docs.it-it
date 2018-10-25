---
title: EXCEPTION_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bbefc02a05d03dc966c05941ca08c05cce0a5a5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947914"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Descrive un'eccezione o errore di run-time generato dal programma in fase di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Membri  
 pProgram  
 Il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma in cui si è verificata l'eccezione.  
  
 bstrProgramName  
 Il nome del programma in cui si è verificata l'eccezione.  
  
 bstrExceptionName  
 Il nome dell'eccezione.  
  
 dwCode  
 Il codice di identificazione per errore eccezione o di run-time.  
  
 dwState  
 Un valore compreso il [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) enumerazione che definisce lo stato dell'eccezione.  
  
 guidType  
 L'identificatore di lingua GUID, ad esempio `guidLang` o `guidEng`.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata come parametro per il [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) e il [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) metodi. Questa struttura viene inoltre passata per il [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) metodo deve essere compilato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)