---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0fa2299e47924a10a6d0b02a982535865164191
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160167"
---
# <a name="frameinfo"></a>FRAMEINFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrive un stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```csharp  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## <a name="members"></a>Membri  
 m_dwValidFields  
 Combinazione di flag dell'enumerazione [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) che specifica i campi che vengono compilati.  
  
 m_bstrFuncName  
 Nome della funzione associato all'stack frame.  
  
 m_bstrReturnType  
 Tipo restituito associato all'stack frame.  
  
 m_bstrArgs  
 Argomenti per la funzione associata all'stack frame.  
  
 m_bstrLanguage  
 Lingua in cui è implementata la funzione.  
  
 m_bstrModule  
 Nome del modulo associato all'stack frame.  
  
 m_addrMin  
 Indirizzo dello stack fisico minimo.  
  
 m_addrMAX  
 Indirizzo massimo dello stack fisico.  
  
 m_pFrame  
 Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta questo stack frame.  
  
 m_pFrame  
 Oggetto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che rappresenta il modulo che contiene questo stack frame.  
  
 m_fHasDebugInfo  
 Diverso da zero ( `TRUE` ) se le informazioni di debug esistono nel frame specificato.  
  
 m_fHasDebugInfo  
 Diverso da zero ( `TRUE` ) se l'stack frame è associato a codice che non è più valido.  
  
 m_fHasDebugInfo  
 Diverso da zero ( `TRUE` ) se il stack frame viene annotato da gestione debug sessione (SDM).  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene passata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) da compilare. Questa struttura è inoltre contenuta in un elenco contenuto nell'interfaccia [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) che, a sua volta, viene restituito da una chiamata al metodo [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
