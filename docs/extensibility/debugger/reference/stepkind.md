---
description: Specifica il tipo di passaggio per l'esecuzione di istruzioni.
title: STEPKIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a972617b071f3c6f45a289a5fc01647bf3adee7fd9ebfa4ba4e2712c4774816
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276178"
---
# <a name="stepkind"></a>STEPKIND
Specifica il tipo di passaggio per l'esecuzione di istruzioni.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Campi
 `STEP_INTO`\
 Passaggi in una funzione.

 `STEP_OVER`\
 Passaggi su una funzione.

 `STEP_OUT`\
 Esce da una funzione.

 `STEP_BACKWARDS`\
 Consente di tornare indietro in una funzione.

## <a name="remarks"></a>Commenti
 Passato come argomento al [metodo Step.](../../../extensibility/debugger/reference/idebugprocess3-step.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
