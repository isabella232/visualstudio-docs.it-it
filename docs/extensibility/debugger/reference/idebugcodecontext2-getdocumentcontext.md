---
description: Ottiene il contesto del documento che corrisponde a questo contesto di codice.
title: Interfaccia IDebugCodeContext2::GetDocumentContext | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9aadc89257d86bac9432026d368c1f84e963152a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079831"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ottiene il contesto del documento che corrisponde a questo contesto di codice. Il contesto del documento rappresenta una posizione nel file di origine corrispondente al codice sorgente che ha generato questa istruzione.

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
[out] Restituisce [l'oggetto IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che corrisponde al contesto del codice. Se `S_OK` viene restituito , ths deve essere diverso da `null` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un motore di debug deve restituire un codice di errore, ad esempio quando il parametro è, ad esempio, quando il `E_FAIL` contesto del codice non ha una posizione di origine `out` `null` associata.

## <a name="remarks"></a>Commenti
 In genere, il contesto del documento può essere considerato come una posizione in un file di origine, mentre il contesto di codice è una posizione di un'istruzione di codice in un flusso di esecuzione.

## <a name="see-also"></a>Vedi anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
