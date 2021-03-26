---
description: Questo metodo ottiene il tipo di campo della classe che rappresenta un nome di classe completo.
title: 'IDebugSymbolProvider:: GetClassTypeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6439200ce0865fe7e6efd2424be0c5798e02dfa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081360"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Questo metodo ottiene il tipo di campo della classe che rappresenta un nome di classe completo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetClassTypeByName( 
   LPCOLESTR          pszClassName,
   NAME_MATCH         nameMatch,
   IDebugClassField** ppField
);
```

```csharp
int GetClassTypeByName(
   string               pszClassName,
   NAME_MATCH           nameMatch,
   out IDebugClassField ppField
);
```

## <a name="parameters"></a>Parametri
`pszClassName`\
in Nome della classe.

`nameMatch`\
in Consente di selezionare il tipo di corrispondenza, ad esempio con distinzione tra maiuscole e minuscole. Valore dell'enumerazione [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) .

`ppField`\
out Restituisce il tipo di classe come rappresentato dall'interfaccia [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
