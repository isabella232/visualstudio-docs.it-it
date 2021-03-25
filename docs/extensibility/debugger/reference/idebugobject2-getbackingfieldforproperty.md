---
description: Ottiene il campo o la variabile, se presente, che può eseguire il backup della proprietà rappresentata da questo oggetto.
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 210381e034ccae8ab9662b77c47970af2affa095
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053802"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ottiene il campo o la variabile, se presente, che può eseguire il backup della proprietà rappresentata da questo oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametri
`ppObject`\
out Oggetto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) che descrive il campo sottostante.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 L'oggetto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) rappresenta una proprietà della classe di codice gestito, ovvero un metodo con una funzione di accesso get e/o set. Tali proprietà richiedono in genere una variabile per contenere il valore modificato dalla proprietà. Questa variabile è nota come campo sottostante. Se non è presente alcun campo di supporto per l'oggetto, assicurarsi di restituire un valore null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma cercheranno invece di verificare se è stato restituito un valore null in `ppObject` .

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
