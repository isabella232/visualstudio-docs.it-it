---
description: Ottiene l'intervallo di codice sorgente di questo contesto del documento.
title: 'IDebugDocumentContext2:: GetSourceRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d02dfbd93002bedadd4c82168d498f89050ddc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162901"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Ottiene l'intervallo di codice sorgente di questo contesto del documento.

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
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) compilata con la posizione iniziale. Se queste informazioni non sono necessarie, impostare questo argomento su un valore null.

`pEndPosition`\
[in, out] Struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) compilata con la posizione finale. Se queste informazioni non sono necessarie, impostare questo argomento su un valore null.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un intervallo di origine è l'intero intervallo di codice sorgente, dall'istruzione corrente di nuovo a subito dopo l'istruzione precedente che ha fornito il codice. L'intervallo di origine viene in genere usato per combinare le istruzioni di origine, inclusi i commenti, con il codice nella finestra Disassembly.

 Per ottenere l'intervallo solo per le istruzioni di codice contenute in questo contesto del documento, chiamare il metodo [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
