---
description: Imposta il provider di servizi.
title: Interfaccia IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9cfc443f7c70949c2b5a12d64fd1c93aadd8160
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072219"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Imposta il provider di servizi.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>Parametri
`pSP`\
[in] Riferimento all'interfaccia del provider di servizi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo verrà chiamato prima di qualsiasi altro metodo.

## <a name="see-also"></a>Vedi anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
