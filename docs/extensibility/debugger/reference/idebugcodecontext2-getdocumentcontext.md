---
description: Ottiene il contesto del documento che corrisponde a questo contesto del codice.
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80420f12369ef038c2faccb51c9b1bfc9b0073a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088419"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ottiene il contesto del documento che corrisponde a questo contesto del codice. Il contesto del documento rappresenta una posizione nel file di origine che corrisponde al codice sorgente che ha generato questa istruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parametri
`ppSrcCxt`\
out Restituisce l'oggetto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che corrisponde al contesto del codice. Se `S_OK` viene restituito, THS deve essere non `null` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un motore di debug deve restituire un codice di errore, ad esempio `E_FAIL` quando il `out` parametro è `null` , ad esempio quando al contesto del codice non è associata una posizione di origine.

## <a name="remarks"></a>Commenti
 In genere, il contesto del documento può essere considerato come una posizione in un file di origine mentre il contesto del codice è una posizione di un'istruzione di codice in un flusso di esecuzione.

## <a name="see-also"></a>Vedi anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
