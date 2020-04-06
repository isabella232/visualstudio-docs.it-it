---
title: PROPRIETÀ FRAMEINFO . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c40361a9739bf468de2038df4325fa1ac98337c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736790"
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
`m_dwValidFields`\
Combinazione di flag dell'enumerazione [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) che specifica i campi da compilare.

`m_bstrFuncName`\
Nome della funzione associata allo stack frame.

`m_bstrReturnType`\
Tipo restituito associato allo stack frame.

`m_bstrArgs`\
Argomenti della funzione associata allo stack frame.

`m_bstrLanguage`\
Linguaggio in cui viene implementata la funzione.

`m_bstrModule`\
Nome del modulo associato allo stack frame.

`m_addrMin`\
Indirizzo minimo dello stack fisico.

`m_addrMAX`\
Indirizzo massimo dello stack fisico.

`m_pFrame`\
Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta questo stack frame.

`m_pModule`\
Oggetto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che rappresenta il modulo che contiene questo stack frame.

`m_fHasDebugInfo`\
Diverso da`TRUE`zero ( ) se le informazioni di debug sono presenti nel frame specificato.

`m_fStaleCode`\
Diverso da`TRUE`zero ( ) se lo stack frame è associato a codice non più valido.

`m_fAnnotatedFrame`\
Diverso da`TRUE`zero ( ) se lo stack frame è annotato dal gestore di debug della sessione (SDM).

## <a name="remarks"></a>Osservazioni
Questa struttura viene passata al [metodo GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) da compilare. Questa struttura è contenuta anche in un elenco contenuto nel [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaccia che, a sua volta, viene restituito da una chiamata al [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metodo.

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
