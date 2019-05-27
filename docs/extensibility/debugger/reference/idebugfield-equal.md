---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfee65537512398cad2f4b86d51ebefac230fb1c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212232"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Questo metodo confronta questo campo con il campo specificato per verificarne l'uguaglianza.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parametri
`pField`\
[in] Campo da confrontare con questo.

## <a name="return-value"></a>Valore restituito
 Se i campi sono uguali, restituisce `S_OK`. Se i campi sono diversi, restituisce `S_FALSE.` in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)