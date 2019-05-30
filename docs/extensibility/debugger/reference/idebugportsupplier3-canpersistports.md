---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11bc6e21e8b70a5bd95c001f4173a7da3f3fe4be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340063"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Questo metodo determina se il fornitore della porta può mantenere le porte (mediante la scrittura su disco) tra le chiamate del debugger.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametri
 Nessuno.

## <a name="return-value"></a>Valore restituito
 `S_OK` Se le porte possono essere resi persistenti, o `S_FALSE` per indicare che le porte non possono essere persistente.

## <a name="remarks"></a>Note
 Se il fornitore della porta può rendere persistenti le porte, dovrebbe eseguire questa operazione quando viene eliminata e quindi ricaricarli quando ne viene creata un'istanza ancora una volta.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)