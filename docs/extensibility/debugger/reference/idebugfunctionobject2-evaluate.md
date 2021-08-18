---
description: IDebugFunctionObject2::Evaluate chiama la funzione e restituisce il valore risultante come oggetto .
title: IDebugFunctionObject2::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 86139b29b08fde8141dc905e98047a29520e6362
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088614"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Chiama la funzione e restituisce il valore risultante come oggetto .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametri
`ppParams`\
[in] Matrice di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta i parametri di input. Ognuno di questi parametri è stato creato usando uno dei metodi Create in questa interfaccia.

`dwParams`\
[in] Numero di parametri nella `ppParams` matrice.

`dwEvalFlags`\
[in] Combinazione di flag [dell'enumerazione EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Usare **INFINITE** per attendere a tempo indeterminato.

`ppResult`\
[out] Restituisce un **oggetto IDebugObject** che rappresenta il valore della funzione come oggetto .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
