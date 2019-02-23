---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad31d015048d8e0732c32652141b7be060628663
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722629"
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

#### <a name="parameters"></a>Parametri
 Nessuno.

## <a name="return-value"></a>Valore restituito
 `S_OK` Se le porte possono essere resi persistenti, o `S_FALSE` per indicare che le porte non possono essere persistente.

## <a name="remarks"></a>Note
 Se il fornitore della porta può rendere persistenti le porte, dovrebbe eseguire questa operazione quando viene eliminata e quindi ricaricarli quando ne viene creata un'istanza ancora una volta.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)