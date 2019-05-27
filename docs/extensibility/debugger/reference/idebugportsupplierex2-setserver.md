---
title: IDebugPortSupplierEx2::SetServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2::SetServer
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e92ee346a5d503c004279df84bdd8aacc429337
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204245"
---
# <a name="idebugportsupplierex2setserver"></a>IDebugPortSupplierEx2::SetServer
Imposta il server principale per il fornitore della porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetServer(
   IDebugCoreServer2* pServer
);
```

```csharp
int SetServer(
   IDebugCoreServer2 pServer
);
```

## <a name="parameters"></a>Parametri
`pServer`\
Server core da impostare per il fornitore della porta.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)