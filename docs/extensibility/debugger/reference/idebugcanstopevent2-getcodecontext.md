---
title: 'IDebugCanStopEvent2:: GetCodeContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aefce11ba82cae7529ed1127784d70771add8302
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919977"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Ottiene il contesto del codice che descrive la posizione di questo evento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCodeContext( 
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametri
`ppCodeContext`\
out Restituisce l'oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta la posizione del codice corrente.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per la maggior parte delle architetture in fase di esecuzione, un contesto di codice può essere considerato come un indirizzo nel flusso di esecuzione di un programma, puntando a un'istruzione specifica.

 Per ottenere il contesto del documento, che è orientato verso le righe del codice sorgente, chiamare il metodo [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
