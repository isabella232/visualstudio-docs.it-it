---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536386"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ottiene il campo o una variabile (se presente) che può essere supporta la proprietà rappresentata da questo oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

#### <a name="parameters"></a>Parametri
 `ppObject`

 [out] Un' [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto che descrive il campo sottostante.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto rappresenta una proprietà di classe di codice gestito, vale a dire, un metodo con una richiesta get e/o funzione di accesso set. Tali proprietà richiedono in genere una variabile per contenere il valore modificato dalla proprietà. Questa variabile è noto come il campo sottostante. Se è presente alcun campo sottostante per l'oggetto, quindi assicurarsi di restituire un valore null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma avrà un aspetto invece per vedere se è stato restituito un valore null in `ppObject`.

## <a name="see-also"></a>Vedere anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)