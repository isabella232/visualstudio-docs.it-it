---
title: IDebugBinder3::GetTypeArguments | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b82c5befe302c88e9f687bd2e6be7195dc4757cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531752"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugBinder3::GetTypeArguments](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-gettypearguments).

Questo metodo recupera un elenco dei tipi di argomento associato all'oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

#### <a name="parameters"></a>Parametri

 `skip`

 [in] Numero di campi da ignorare prima di ottenere i tipi di argomento.

 `count`

 [in] Il numero di campi dell'argomento da restituire (specifica anche la dimensione del `ppFields` matrice).

 `ppFields`

 [in, out] Matrice di campi che verranno compilati in fase di restituzione di questo metodo.

 `pFetched`

 [out] Il numero di campi dei tipi di argomento ha effettivamente restituito (facoltativo).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 È possibile ottenere in anticipo il numero di tipi di argomento con [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).

## <a name="see-also"></a>Vedere anche

- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)