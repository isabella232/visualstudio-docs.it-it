---
description: Ottiene il contesto del documento per questo stack frame.
title: IDebugStackFrame2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96979c45471aab356a22f206698e50e238009bb54bea0edc02db5bacad1e6464
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448949"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
Ottiene il contesto del documento per questo stack frame.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppCxt
);
```

## <a name="parameters"></a>Parametri
`ppCxt`\
[out] Restituisce un [oggetto IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che rappresenta la posizione corrente in un documento di origine.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo è più veloce rispetto alla [chiamata al metodo GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) e quindi alla chiamata del [metodo GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) nel contesto del codice. Tuttavia, non è garantito che ogni motore di debug implementerà questo metodo.

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
