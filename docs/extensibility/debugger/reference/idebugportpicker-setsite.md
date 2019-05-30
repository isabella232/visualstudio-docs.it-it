---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d6d12bd21a6ab208fed019c1e0f763bce86724
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340354"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Imposta il provider del servizio.

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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo verrà chiamato prima degli altri metodi vengono chiamati.

## <a name="see-also"></a>Vedere anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)