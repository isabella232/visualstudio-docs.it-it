---
title: 'IDebugField:: EQUAL | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c19e8860fb9ed9cbd65efe7fa72fd920a01622ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915477"
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
in Campo da confrontare con questo.

## <a name="return-value"></a>Valore restituito
 Se i campi sono uguali, restituisce `S_OK` . Se i campi sono diversi, restituisce `S_FALSE.` in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
