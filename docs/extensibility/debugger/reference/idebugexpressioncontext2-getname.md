---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d53d7f497700d4e23587927adc0c2cee37824daa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325870"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Recupera il nome del contesto di valutazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
[out] Restituisce il nome del contesto di valutazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il nome è la descrizione di questo contesto di valutazione. È in genere qualcosa che può essere analizzato da un analizzatore di espressioni che fa riferimento a questo contesto di valutazione esatta. Ad esempio, in C++ il nome è come segue:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)