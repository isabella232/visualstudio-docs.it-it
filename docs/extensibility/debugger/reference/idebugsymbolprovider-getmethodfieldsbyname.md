---
description: Questo metodo ottiene il campo che rappresenta il nome completo di un metodo.
title: 'IDebugSymbolProvider:: GetMethodFieldsByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54962d87bcb3de471c9799f4c6be9f969b8eed17
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087002"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Questo metodo ottiene il campo che rappresenta il nome completo di un metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`pszFullName`\
in Nome del metodo.

`nameMatch`\
in Consente di selezionare il tipo di corrispondenza, ad esempio con distinzione tra maiuscole e minuscole.

`ppEnum`\
out Restituisce un enumeratore [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) per i campi associati a questo metodo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un metodo può essere associato a più campi se è in overload, ad esempio.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
