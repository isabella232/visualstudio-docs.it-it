---
title: FRAMEINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84e7329acb3cdbff5c2f84fbd035867791012b2e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680503"
---
# <a name="frameinfo"></a>FRAMEINFO
Descrive uno stack frame.

## <a name="syntax"></a>Sintassi

```cpp
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
m_dwValidFields una combinazione di flag dal [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumerazione che specifica quali campi vengono compilati.

m_bstrFuncName associati il nome della funzione con lo stack frame.

m_bstrReturnType il tipo restituito associato al frame dello stack.

m_bstrArgs gli argomenti alla funzione associato al frame dello stack.

m_bstrLanguage la lingua in cui la funzione è implementata.

m_bstrModule il nome del modulo associata al frame dello stack.

m_addrMin l'indirizzo dello stack fisico minimo.

m_addrMAX l'indirizzo massima dello stack fisico.

m_pFrame il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) oggetto che rappresenta lo stack frame corrente.

m_pFrame il [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) oggetto che rappresenta il modulo che contiene questo stack frame.

m_fHasDebugInfo diverso da zero (`TRUE`) se le informazioni di debug è presente nel frame specificato.

m_fHasDebugInfo diverso da zero (`TRUE`) se il frame dello stack è associato il codice che non è più valido.

m_fHasDebugInfo diverso da zero (`TRUE`) se il frame dello stack è annotato dal gestore di sessione di debug (SDM).

## <a name="remarks"></a>Note
Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metodo deve essere compilato. Questa struttura anch ' essa contenuta in un elenco di contenuto nel [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia che, a sua volta, viene restituito da una chiamata ai [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
