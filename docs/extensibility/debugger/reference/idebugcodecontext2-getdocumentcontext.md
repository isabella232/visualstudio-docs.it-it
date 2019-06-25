---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a12838db0687fd7ebe20a5c576db0e06ece49107
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342404"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ottiene il contesto del documento che corrisponde a questo contesto di codice. Il contesto del documento rappresenta una posizione nel file di origine che corrisponde al codice sorgente che ha generato questa istruzione.

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
[out] Restituisce il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetto corrispondente nel contesto del codice. Se `S_OK` viene restituito, deve essere ths non`null`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Un motore di debug deve restituire un codice di errore, ad esempio `E_FAIL` quando il `out` parametro è `null` , ad esempio quando il contesto del codice non ha nessuna posizione di origine associata.

## <a name="remarks"></a>Note
 In genere, il contesto del documento può essere considerato come una posizione in un file di origine mentre il contesto del codice è una posizione di un'istruzione di codice in un flusso di esecuzione.

## <a name="see-also"></a>Vedere anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
