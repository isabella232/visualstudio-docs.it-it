---
description: Questa struttura viene utilizzata per impostare le informazioni JustMyCode per un modulo.
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9bb05d55268d3f0ef497831616b8e27aae4bb86
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058079"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Questa struttura viene utilizzata per impostare le informazioni JustMyCode per un modulo.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Members
`fIsUserCode`\
Diverso da zero ( `TRUE` ) se il modulo deve essere considerato codice utente; in caso contrario, zero ( `FALSE` ) se il modulo deve essere trattato come codice esterno e non deve essere sottoposto a debug.

`bstrModuleName`\
Nome del modulo in questione.

## <a name="remarks"></a>Commenti
Questa struttura viene passata come un elenco di tali strutture al metodo [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
