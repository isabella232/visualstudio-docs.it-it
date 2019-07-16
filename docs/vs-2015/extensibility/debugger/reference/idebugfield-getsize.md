---
title: IDebugField::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9fded9abc006ff6a28e122f0a4b8d7fae5da997b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148925"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Questo metodo ottiene le dimensioni di un campo, in byte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

#### <a name="parameters"></a>Parametri
 `pdwSize`

 [out] Restituisce la dimensione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Tutti i campi hanno un tipo e tutti i tipi hanno una dimensione. Ad esempio, un campo con un tipo di byte ha una dimensione di 1 byte.

## <a name="see-also"></a>Vedere anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)