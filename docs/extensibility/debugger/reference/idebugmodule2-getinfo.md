---
description: Ottiene informazioni su questo modulo.
title: IDebugModule2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b353ff5f219364ef63a36bea9d52323051a4cf62e0beccaf702555b4ec6f8b53
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433502"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Ottiene informazioni su questo modulo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag [dell'MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) che specificano quali campi di `pInfo` devono essere compilati.

`pInfo`\
[in, out] Struttura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) che viene compilata con una descrizione del modulo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) contiene il nome del modulo visualizzato nella **finestra** Moduli.

## <a name="see-also"></a>Vedi anche
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
