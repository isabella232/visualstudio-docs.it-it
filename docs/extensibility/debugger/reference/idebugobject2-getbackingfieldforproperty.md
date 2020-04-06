---
title: Proprietà IDebugObject2::GetBackingFieldForProperty . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726251"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ottiene il campo o la variabile (se presente) che può sostenere la proprietà rappresentata da questo oggetto.

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

## <a name="parameters"></a>Parametri
`ppObject`\
[fuori] Oggetto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) che descrive il campo di base.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Il [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto rappresenta una proprietà della classe di codice gestito, vale a dire, un metodo con una funzione di accesso get e/o set. Tali proprietà richiedono in genere una variabile per contenere il valore modificato dalla proprietà. Questa variabile è nota come campo di backup. Se non è presente alcun campo di supporto per l'oggetto, assicurarsi di restituire un valore null: alcuni chiamanti potrebbero non `ppObject`prestare attenzione al valore restituito, ma cercheranno invece di vedere se è stato restituito un valore null in .

## <a name="see-also"></a>Vedere anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
