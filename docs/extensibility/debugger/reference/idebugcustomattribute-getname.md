---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed12526422a38b7b3b629a0acafc019b2e94a5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62921882"
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

#### <a name="parameters"></a>Parametri
 `bstrName`

 [out] Restituisce una stringa contenente il nome dell'attributo personalizzato.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'oggetto restituito da questo metodo denominato corrisponde al nome della classe utilizzata per dichiarare l'attributo. Ciò non è uguale a può corrispondere al nome della classe dell'attributo personalizzato come c# consente il suffisso "Attribute" che si desidera eliminare da un nome di attributo personalizzato quando viene usata in una dichiarazione.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)