---
description: Recupera una porta specifica.
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 61529eea2c68d5504cae9ad29ffc467d09751c9ec35db8cb3953ee4410b57ed9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239009"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Recupera una porta specifica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parametri
`guidPort`\
[in] GUID della porta da recuperare.

`ppPort`\
[out] Restituisce un [oggetto IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta desiderata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_PORTSUPPLIER_NO_PORT` se non è presente alcuna porta con l'identificatore specificato.

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
