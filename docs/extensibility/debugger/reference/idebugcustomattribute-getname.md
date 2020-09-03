---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732767"
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

## <a name="remarks"></a>Osservazioni
 Il denominato restituito da questo metodo corrisponde al nome della classe utilizzata per dichiarare l'attributo. Questo potrebbe non corrispondere esattamente al nome della classe di attributi personalizzati perché C# consente il rilascio del suffisso "Attribute" da un nome di attributo personalizzato quando viene usato in una dichiarazione.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
