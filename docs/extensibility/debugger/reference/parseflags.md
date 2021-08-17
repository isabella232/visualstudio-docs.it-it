---
description: Specifica come analizzare un'espressione.
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4c279bdadb692007a66eed38ccd595d94be3c05f5c2777a3a30eae6af33666c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433086"
---
# <a name="parseflags"></a>PARSEFLAGS
Specifica come analizzare un'espressione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Campi
 `PARSE_EXPRESSION`\
 Indica che l'espressione non è un'istruzione .

 `PARSE_FUNCTION_AS_ADDRESS`\
 Indica che l'espressione deve essere analizzata (e valutata successivamente) come indirizzo.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Indica che l'espressione viene analizzata durante la fase di progettazione, ovvero quando è aperta una finestra di progettazione.

## <a name="remarks"></a>Commenti
 Passato come parametro ai [metodi ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) [e Parse.](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md).
