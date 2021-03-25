---
description: Ottiene il nome del documento in uno dei diversi formati.
title: 'IDebugDocument2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49c9a2b4fd95fbb24b28b69003c8e462b09be38b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066815"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Ottiene il nome del documento in uno dei diversi formati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parametri
`gnType`\
in Valore dell'enumerazione [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) che determina il tipo di nome da restituire.

`pbstrFileName`\
out Restituisce una stringa contenente il nome del documento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo può, ad esempio, restituire il nome del documento come titolo o come nome file o anche parte di un nome file.

## <a name="see-also"></a>Vedi anche
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
