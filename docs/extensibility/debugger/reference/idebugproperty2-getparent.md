---
description: Ottiene la proprietà padre di una proprietà.
title: IDebugProperty2::GetParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32617d8be165bfa09b80460464c62dbae1c12ea9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050507"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Ottiene la proprietà padre di una proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

## <a name="parameters"></a>Parametri
`ppParent`\
[out] Restituisce un [oggetto IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta l'elemento padre della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore. Restituisce `S_GETPARENT_NO_PARENT` se non esiste alcun padre.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
