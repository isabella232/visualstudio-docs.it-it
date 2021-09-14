---
description: Ottiene l'intervallo di codice sorgente del contesto del documento.
title: Interfaccia IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0eeec0f04f45cda0c257299923f0da9224312974
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635027"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ottiene l'intervallo di codice sorgente del contesto del documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametri
`pBegPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che viene compilata con la posizione iniziale. Impostare questo argomento su un valore Null se queste informazioni non sono necessarie.

`pEndPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che viene compilata con la posizione finale. Impostare questo argomento su un valore Null se queste informazioni non sono necessarie.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un intervallo di origine è l'intero intervallo di codice sorgente, dall'istruzione corrente fino all'istruzione precedente che ha contribuito al codice. L'intervallo di origine viene in genere usato per combinare le istruzioni di origine, inclusi i commenti, con il codice nella finestra disassembly.

 Per ottenere l'intervallo solo per le istruzioni di codice contenute nel contesto del documento, chiamare il [metodo GetStatementRange.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
