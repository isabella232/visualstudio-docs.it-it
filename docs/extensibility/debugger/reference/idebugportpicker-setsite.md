---
description: Imposta il provider di servizi.
title: 'IDebugPortPicker:: SESITE | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a442c438f233187265c90e724f57e8681b95556
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072259"
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
in Riferimento all'interfaccia del provider di servizi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo verrà chiamato prima della chiamata di altri metodi.

## <a name="see-also"></a>Vedi anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
