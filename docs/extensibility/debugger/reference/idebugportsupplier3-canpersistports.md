---
description: Questo metodo determina se il fornitore della porta può salvare in modo permanente le porte (scrivendole su disco) tra le chiamate del debugger.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172009"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Questo metodo determina se il fornitore della porta può salvare in modo permanente le porte (scrivendole su disco) tra le chiamate del debugger.

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
 `S_OK` Se le porte possono essere rese permanente oppure `S_FALSE` per indicare che le porte non possono essere rese permanente.

## <a name="remarks"></a>Commenti
 Se il fornitore della porta può rendere permanente le porte, questa operazione viene eseguita quando viene distrutta e quindi ricaricata quando ne viene creata un'istanza ancora una volta.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
