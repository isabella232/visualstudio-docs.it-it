---
description: Descrive una stack frame.
title: FrameINFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c2f2da572c18dfce5aac6a8aa748a07347ff088
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104612"
---
# <a name="frameinfo"></a>FRAMEINFO
Descrive una stack frame.

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

## <a name="members"></a>Members
`m_dwValidFields`\
Combinazione di flag [dell'FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) che specifica quali campi vengono compilati.

`m_bstrFuncName`\
Nome della funzione associato all'stack frame.

`m_bstrReturnType`\
Tipo restituito associato all'stack frame.

`m_bstrArgs`\
Argomenti per la funzione associata all'stack frame.

`m_bstrLanguage`\
Linguaggio in cui viene implementata la funzione.

`m_bstrModule`\
Nome del modulo associato all'stack frame.

`m_addrMin`\
Indirizzo minimo dello stack fisico.

`m_addrMAX`\
Indirizzo massimo dello stack fisico.

`m_pFrame`\
Oggetto [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che rappresenta questa stack frame.

`m_pModule`\
Oggetto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che rappresenta il modulo che contiene questo stack frame.

`m_fHasDebugInfo`\
Diverso da zero ( `TRUE` ) se nel frame specificato sono presenti informazioni di debug.

`m_fStaleCode`\
Diverso da zero ( `TRUE` ) se il stack frame è associato a codice non più valido.

`m_fAnnotatedFrame`\
Diverso da zero ( `TRUE` ) se il stack frame è annotato dalla gestione del debug di sessione (SDM).

## <a name="remarks"></a>Commenti
Questa struttura viene passata [al metodo GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) da completare. Questa struttura è contenuta anche in un elenco contenuto nell'interfaccia [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) che, a sua volta, viene restituita da una chiamata al [metodo EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
