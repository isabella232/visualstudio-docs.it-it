---
title: IDebugCanStopEvent2::GetCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d11a8a5bf3a0fc66487b8a0e58cd98aefdbd255
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713906"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Ottiene il contesto di codice che descrive la posizione di questo evento.

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

#### <a name="parameters"></a>Parametri
 `ppCodeContext`

 [out] Restituisce il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che rappresenta il percorso di codice corrente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Per la maggior parte delle architetture di runtime, un contesto del codice può essere considerato come un indirizzo nel flusso di esecuzione del programma, sta puntando a un'istruzione specifica.

 Per ottenere il contesto del documento, che è orientato verso le righe di codice sorgente, chiamare il [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)