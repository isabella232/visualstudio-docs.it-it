---
description: Restituisce un identificatore di posizione del codice per un particolare contesto di codice.
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f68ee6ff0495fe36d8de8ccf0e3c2c81f3d05ac5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067088"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Restituisce un identificatore di posizione del codice per un particolare contesto di codice.

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
in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) da convertire in un identificatore.

`puCodeLocationId` out Restituisce l'identificatore della posizione del codice. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_CODE_CONTEXT_OUT_OF_SCOPE` se il contesto del codice è valido ma esterno all'ambito.

## <a name="remarks"></a>Commenti
 L'identificatore del percorso del codice è specifico del motore di debug (DE) che supporta il disassembly. Questo identificatore di percorso viene utilizzato internamente da DE per tenere traccia delle posizioni nel codice ed è in genere un indirizzo o un offset di qualche tipo. L'unico requisito è che se il contesto del codice di una posizione è inferiore al contesto del codice di un'altra posizione, l'identificatore del percorso di codice corrispondente del primo contesto di codice deve essere minore di quello del secondo contesto di codice.

 Per recuperare il contesto del codice di un identificatore del percorso di codice, chiamare il metodo [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
