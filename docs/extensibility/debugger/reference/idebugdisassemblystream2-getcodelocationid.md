---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58e3b12ecbc75b7d07d60ac399412dc5b0deb73b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351689"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Restituisce un identificatore percorso codice per un contesto di codice specifico.

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
[in] Un' [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto da convertire in un identificatore.

`puCodeLocationId` [out] Restituisce l'identificatore percorso codice. Vedere la sezione Osservazioni.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_CODE_CONTEXT_OUT_OF_SCOPE` se il contesto del codice è valido, ma all'esterno dell'ambito.

## <a name="remarks"></a>Note
 L'identificatore percorso codice è specifico per il motore di debug (DE) che supporta il disassembly. Questo identificatore di località viene utilizzato internamente per la Germania per tenere traccia delle posizioni nel codice e in genere è un indirizzo o un offset di qualche tipo. L'unico requisito è che se il contesto del codice di un'unica posizione è inferiore al contesto del codice di un'altra posizione, l'identificatore percorso codice corrispondente del primo contesto di codice deve essere anche minore l'identificatore percorso codice il secondo contesto del codice.

 Per recuperare il contesto del codice di un identificatore percorso codice, chiamare il [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)