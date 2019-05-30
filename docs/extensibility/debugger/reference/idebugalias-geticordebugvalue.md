---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50fb7800c4446e7d13334957ee9f5f6534f254bf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338218"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera un'interfaccia di codice gestito che rappresenta il valore associato a questo alias.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametri
`ppUnk`\
[out] `IUnknown` interfaccia che rappresenta il valore associato a questo alias. Questa interfaccia è possibile eseguire query per il `ICorDebugValue` interfaccia.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo si applica solo ai valori gestiti (il `ICorDebugValue` è disponibile in un'interfaccia di [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] e viene definito nel [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK nel file Cordebug. idl).

## <a name="see-also"></a>Vedere anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)