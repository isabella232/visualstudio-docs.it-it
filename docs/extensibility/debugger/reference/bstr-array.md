---
description: Struttura che descrive una matrice di stringhe.
title: BSTR_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 43a4b68824b613cb0701ea5ccfb3ed334f715b69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145731"
---
# <a name="bstr_array"></a>BSTR_ARRAY
Struttura che descrive una matrice di stringhe.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>Members
`dwCount`\
Numero di stringhe nella `Members` matrice.

`Members`\
Matrice di stringhe.

## <a name="remarks"></a>Commenti
Questa struttura viene restituita [dal metodo EnumPersistedPorts.](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)

 [Solo C++] Ogni singola stringa deve essere liberata usando `SysFreeString` e la matrice deve essere `Members` liberata con `CoTaskMemFree` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
