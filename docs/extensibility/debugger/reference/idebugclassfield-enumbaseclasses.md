---
description: Crea un enumeratore per le classi di base di questa classe.
title: 'IDebugClassField:: EnumBaseClasses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ba31ead00ad2312b66273a2ddfaeebd252e0981
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084987"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
Crea un enumeratore per le classi di base di questa classe.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\

out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di classi di base. Restituisce un valore null se non sono disponibili classi di base.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK, restituisce S_SH_NO_BASE_CLASSES se non sono presenti classi base (e il `ppEnum` parametro è impostato su un valore null); in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Le classi base nell'oggetto enumeratore vengono specificate in ordine della classe di base più immediata (o più derivata) per la classe di base più remota. Ad esempio, date le classi C++:

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 L'enumerazione restituirà le classi base nell'ordine `Level2` , `Level1` , `Root` .

## <a name="see-also"></a>Vedi anche
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
