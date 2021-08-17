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
ms.openlocfilehash: 0d83ca6ffb7899d6a144dc823a5849a41c6188c7569256446ca3688771facfae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389800"
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
