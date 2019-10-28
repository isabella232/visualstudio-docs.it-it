---
title: 'IDebugPort2:: getportaname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortName
helpviewer_keywords:
- IDebugPort2::GetPortName
ms.assetid: 4478b3d5-aa30-4105-8d05-e3bae2f8917a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0a382a77693fc8839721c0cdd139af2dd5208c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727718"
---
# <a name="idebugport2getportname"></a>IDebugPort2::GetPortName
Ottiene il nome della porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPortName( 
   BSTR* pbstrName
);
```

```csharp
int GetPortName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
out Restituisce il nome della porta.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)