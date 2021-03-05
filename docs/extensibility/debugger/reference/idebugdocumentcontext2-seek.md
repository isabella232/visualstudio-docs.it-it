---
description: Sposta il contesto del documento in base a un numero specificato di istruzioni o righe.
title: 'IDebugDocumentContext2:: Seek | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a70b8fac8e084a78b1a29ae941f1d03d6552f860
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162849"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Sposta il contesto del documento in base a un numero specificato di istruzioni o righe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametri
`nCount`\
in Numero di istruzioni o righe da spostare in avanti, a seconda del contesto del documento.

`ppDocContext`\
out Restituisce un nuovo oggetto [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) con la nuova posizione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
