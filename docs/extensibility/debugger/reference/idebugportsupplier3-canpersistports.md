---
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724467"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Questo metodo determina se il fornitore della porta può salvare in modo permanente le porte (scrivendole su disco) tra le chiamate del debugger.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametri
 No.

## <a name="return-value"></a>Valore restituito
 `S_OK` Se le porte possono essere rese permanente oppure `S_FALSE` per indicare che le porte non possono essere rese permanente.

## <a name="remarks"></a>Osservazioni
 Se il fornitore della porta può rendere permanente le porte, questa operazione viene eseguita quando viene distrutta e quindi ricaricata quando ne viene creata un'istanza ancora una volta.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
