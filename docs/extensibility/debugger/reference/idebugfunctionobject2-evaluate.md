---
title: 'IDebugFunctionObject2:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728442"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Chiama la funzione e restituisce il valore risultante come un oggetto.

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
in Matrice di oggetti [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta i parametri di input. Ognuno di questi parametri è stato creato usando uno dei metodi create in questa interfaccia.

`dwParams`\
in Numero di parametri nella `ppParams` matrice.

`dwEvalFlags`\
in Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.

`dwTimeout`\
in Specifica il tempo massimo di attesa, in millisecondi, prima che venga restituito da questo metodo. Usare **infinito** per un'attesa indefinita.

`ppResult`\
out Restituisce un **IDebugObject** che rappresenta il valore della funzione come un oggetto.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
