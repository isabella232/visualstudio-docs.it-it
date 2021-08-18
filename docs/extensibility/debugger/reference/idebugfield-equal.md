---
description: Questo metodo confronta questo campo con il campo specificato per verificane l'uguaglianza.
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9625aa138330f8504dd90371808a62f8c50ee9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138458"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Questo metodo confronta questo campo con il campo specificato per verificane l'uguaglianza.

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
 Se i campi sono uguali, restituisce `S_OK` . Se i campi sono diversi, restituisce `S_FALSE.` Otherwise, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
