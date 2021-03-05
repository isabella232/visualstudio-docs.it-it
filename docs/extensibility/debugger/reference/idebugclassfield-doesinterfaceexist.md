---
description: Determina se una specifica interfaccia è definita nella classe.
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4248b653f5eea43a91d0c78a593431d53f5e68b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173468"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina se una specifica interfaccia è definita nella classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Parametri
`pszInterfaceName`\
in Stringa contenente il nome dell'interfaccia da ricercare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK, restituisce S_FALSE se l'interfaccia non esiste; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo ottiene un'enumerazione di tutte le interfacce e cerca l'interfaccia corrispondente nell'elenco.

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
