---
description: Ottiene il nome dell'attributo personalizzato.
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 807922628249a38400c86001a27498f3c26fafd30c2b2907e8faa2cb09fd2454
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307960"
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
[out] Restituisce una stringa contenente il nome dell'attributo personalizzato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 L'oggetto denominato restituito da questo metodo corrisponde al nome della classe utilizzata per dichiarare l'attributo. Ciò potrebbe non corrispondere esattamente al nome della classe di attributi personalizzati, perché C# consente di eliminare il suffisso "Attribute" da un nome di attributo personalizzato quando viene usato in una dichiarazione.

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
