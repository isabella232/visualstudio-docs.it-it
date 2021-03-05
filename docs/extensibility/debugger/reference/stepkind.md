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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9cb230eac9e8851437614a590615ad2402923f6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225292"
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
 Viene descritta la procedura indietro in una funzione.

## <a name="remarks"></a>Commenti
 Passato come argomento al metodo [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
