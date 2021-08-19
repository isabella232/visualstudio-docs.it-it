---
description: Ottiene il campo o la variabile (se presente) che può eseguire il backup della proprietà rappresentata da questo oggetto .
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1f89f6158620578be58884a764773cb77b930a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043167"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ottiene il campo o la variabile (se presente) che può eseguire il backup della proprietà rappresentata da questo oggetto .

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
[out] Oggetto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) che descrive il campo di backup.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 [L'oggetto IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) rappresenta una proprietà di una classe di codice gestito, ad esempio un metodo con una funzione di accesso get e/o set. Tali proprietà richiedono in genere che una variabile contenga il valore modificato dalla proprietà . Questa variabile è nota come campo di backup. Se non è presente alcun campo di supporto per l'oggetto , assicurarsi di restituire un valore Null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma cerca invece di verificare se è stato restituito un valore Null in `ppObject` .

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
