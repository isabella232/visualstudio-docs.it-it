---
description: Restituisce un identificatore della posizione del codice per un particolare contesto del codice.
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fce5176c8461f9e04859641bf33da9b60bbeb5ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096570"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Restituisce un identificatore della posizione del codice per un particolare contesto del codice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>Parametri
`pCodeContext`\
[in] Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) da convertire in un identificatore.

`puCodeLocationId` [out] Restituisce l'identificatore del percorso del codice. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_CODE_CONTEXT_OUT_OF_SCOPE` se il contesto del codice è valido ma non rientra nell'ambito.

## <a name="remarks"></a>Commenti
 L'identificatore del percorso del codice è specifico del motore di debug (DE) che supporta il disassembly. Questo identificatore di posizione viene usato internamente da DE per tenere traccia delle posizioni nel codice ed è in genere un indirizzo o un offset di qualche tipo. L'unico requisito è che se il contesto del codice di una posizione è minore del contesto del codice di un'altra posizione, anche l'identificatore della posizione del codice corrispondente del primo contesto del codice deve essere minore dell'identificatore della posizione del codice del secondo contesto del codice.

 Per recuperare il contesto del codice di un identificatore di posizione del codice, chiamare il [metodo GetCodeContext.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
