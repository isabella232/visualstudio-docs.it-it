---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6cd0b91491be365a4686265bd698717219df0afb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188400"
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

#### <a name="parameters"></a>Parametri
 `pSP`

 [in] Riferimento all'interfaccia del provider di servizi.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo verrà chiamato prima degli altri metodi vengono chiamati.

## <a name="see-also"></a>Vedere anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)