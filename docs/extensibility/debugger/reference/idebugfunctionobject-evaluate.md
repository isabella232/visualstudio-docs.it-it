---
description: IDebugFunctionObject::Evaluate chiama la funzione e restituisce il valore risultante come oggetto .
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5526282313c6cdc72fe3834e75855463036811e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088666"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Chiama la funzione e restituisce il valore risultante come oggetto .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametri
`ppParams`\
[in] Matrice di [oggetti IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresentano i parametri di input. Ognuno di questi parametri è stato creato con uno dei `Create` metodi [nell'interfaccia IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

`dwParams`\
[in] Numero di parametri nella `ppParams` matrice.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per attendere per un periodo indefinito.

`ppResult`\
[out] Restituisce un [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta il valore della funzione come oggetto .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo configura ed esegue una chiamata alla funzione rappresentata [dall'oggetto IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
