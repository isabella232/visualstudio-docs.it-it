---
description: Elimina definitivamente l'ID univoco associato a questa proprietà, a indicare che al chiamante non interessa più identificare questa proprietà in modo univoco da tutte le altre proprietà.
title: IDebugProperty3::D estroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d3a8784244c35c5beb6c7711e3438d1b54386dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063967"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Elimina definitivamente l'ID univoco associato a questa proprietà, a indicare che al chiamante non interessa più identificare questa proprietà in modo univoco da tutte le altre proprietà.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Se il motore di debug non deve supportare ID univoci per una proprietà (perché ne tiene già traccia internamente in modo univoco), può semplicemente restituire per `E_NOTIMPL` questo metodo.

 Gli ID univoci vengono creati con una chiamata al metodo [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) quando il chiamante vuole assicurarsi che questa proprietà sia identificata in modo univoco tra tutte le altre proprietà.

## <a name="see-also"></a>Vedi anche
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
