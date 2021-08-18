---
description: Questo metodo determina se il fornitore di porte può rendere persistenti le porte (scrivendole su disco) tra le chiamate del debugger.
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66745d6e4230b89eb8a2c3b20823fa93863f66cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050832"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Questo metodo determina se il fornitore di porte può rendere persistenti le porte (scrivendole su disco) tra le chiamate del debugger.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 `S_OK` se le porte possono essere rese persistenti o `S_FALSE` per indicare che non è possibile rendere persistenti le porte.

## <a name="remarks"></a>Commenti
 Se il fornitore della porta può rendere persistenti le porte, è consigliabile farlo quando viene eliminato e quindi ricaricarle quando ne viene creata di nuovo un'istanza.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
