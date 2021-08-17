---
description: Ottiene una porta da un fornitore di porte.
title: IDebugPortSupplier2::GetPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ff5e598d7b038e4658f228d58a823157eabf82e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088172"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Ottiene una porta da un fornitore di porte.

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
[in] Identificatore univoco globale (GUID) della porta.

`ppPort`\
[out] Restituisce un [oggetto IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_PORTSUPPLIER_NO_PORT` se non esiste alcuna porta con l'identificatore specificato.

## <a name="see-also"></a>Vedi anche
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
