---
description: Ottiene il nome dell'attributo personalizzato.
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 313408639b0a93faef0c63c0add92dc1ca2e947b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163057"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ottiene il nome dell'attributo personalizzato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parametri
`bstrName`\
out Restituisce una stringa contenente il nome dell'attributo personalizzato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Il denominato restituito da questo metodo corrisponde al nome della classe utilizzata per dichiarare l'attributo. Questo potrebbe non corrispondere esattamente al nome della classe di attributi personalizzati perché C# consente il rilascio del suffisso "Attribute" da un nome di attributo personalizzato quando viene usato in una dichiarazione.

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
