---
title: IDebugPortSupplierDescription2::GetDescription | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2::GetDescription
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7619421e66b8f6e68c252fd2c2885272003bb6e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339931"
---
# <a name="idebugportsupplierdescription2getdescription"></a>IDebugPortSupplierDescription2::GetDescription
Recupera la descrizione e una descrizione dei metadati per il fornitore della porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDescription(
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,
   BSTR *pbstrText
);
```

```csharp
public int GetDescription(
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,
   out string pbstrText
);
```

## <a name="parameters"></a>Parametri
`pdwFlags`\
[out] Flag di metadati per la descrizione.

`pbstrText`\
[out] Descrizione del fornitore della porta.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)