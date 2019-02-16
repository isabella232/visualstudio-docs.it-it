---
title: CODE_PATH | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e9de8784f568965c1502565971af67be084f95a
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317393"
---
# <a name="codepath"></a>CODE_PATH
Descrive una chiamata di metodo o funzione.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>Membri
bstrName  
Il nome del percorso del codice.

pCode  
Il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che identifica la posizione del codice per eseguire una funzione.

## <a name="remarks"></a>Note
Questa struttura viene utilizzata per implementare l'esecuzione di una funzione. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) restituisce tutte le chiamate dalla posizione corrente nel programma sottoposto a debug. Questa struttura rappresenta una chiamata di questo tipo.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)  
[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)  
[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
