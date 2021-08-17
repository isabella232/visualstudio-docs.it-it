---
description: Questa struttura viene usata per impostare le informazioni di JustMyCode per un modulo.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca44db2c6e6c097cfe26845eb3f60303155257aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042842"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Questa struttura viene usata per impostare le informazioni di JustMyCode per un modulo.

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
Diverso da zero ( ) se il modulo deve essere considerato codice utente; in caso contrario, zero ( ) se il modulo deve essere considerato come codice esterno e non deve essere `TRUE` `FALSE` debug.

`bstrModuleName`\
Nome del modulo in questione.

## <a name="remarks"></a>Commenti
Questa struttura viene passata come elenco di tali strutture al [metodo SetJustMyCodeState.](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
