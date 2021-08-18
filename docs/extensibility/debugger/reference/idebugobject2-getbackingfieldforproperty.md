---
description: Ottiene il campo o la variabile (se presente) che può essere di backup della proprietà rappresentata da questo oggetto .
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
ms.openlocfilehash: 0019f890f8f487d455e92854f812296fa7dffd94fdde62c13505db2ba69bfe4f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339281"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Ottiene il campo o la variabile (se presente) che può essere di backup della proprietà rappresentata da questo oggetto .

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
 [L'oggetto IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) rappresenta una proprietà della classe di codice gestito, ad esempio un metodo con una funzione di accesso get e/o set. Tali proprietà richiedono in genere che una variabile contenga il valore modificato dalla proprietà . Questa variabile è nota come campo di backup. Se non è presente alcun campo di supporto per l'oggetto , assicurarsi di restituire un valore Null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma cerca di verificare se è stato restituito un valore Null in `ppObject` .

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
