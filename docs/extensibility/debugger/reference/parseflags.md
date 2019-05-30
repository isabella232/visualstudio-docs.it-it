---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6123c6438defff596351fff3d1ba31ea52a19f28
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349929"
---
# <a name="parseflags"></a>PARSEFLAGS
Specifica la modalità di analisi dell'espressione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Campi
 `PARSE_EXPRESSION`\
 Indica che l'espressione non è un'istruzione.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indica che l'espressione deve essere analizzato (e valutate in un secondo momento) come un indirizzo.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indica che l'espressione viene analizzato durante la fase di progettazione (ovvero, quando una finestra di progettazione è aperto).

## <a name="remarks"></a>Note
 Passato come parametro per il [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metodi.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Analisi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)