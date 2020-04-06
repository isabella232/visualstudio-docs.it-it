---
title: IDebugCodeContext2::GetDocumentContext . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734338"
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
[fuori] Restituisce il [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) oggetto che corrisponde al contesto del codice. Se `S_OK` viene restituito, ths deve`null`essere diverso da - .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un motore di debug deve `E_FAIL` restituire `out` un `null` codice di errore, ad esempio quando il parametro è, ad esempio quando il contesto del codice non è associata alcuna posizione di origine.

## <a name="remarks"></a>Osservazioni
 In genere, il contesto del documento può essere considerato come una posizione in un file di origine mentre il contesto di codice è una posizione di un'istruzione di codice in un flusso di esecuzione.

## <a name="see-also"></a>Vedere anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
