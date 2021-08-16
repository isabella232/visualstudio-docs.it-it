---
description: Questo metodo recupera un elenco di tipi di argomento associati a questo oggetto.
title: IDebugBinder3::GetTypeArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fa3de2f8fc505aa6baaffd5c4370ef407c09029a33f9d2c2c14d02b8174f8e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262425"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Questo metodo recupera un elenco di tipi di argomento associati a questo oggetto.

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

## <a name="parameters"></a>Parametri
`skip`\
[in] Numero di campi da ignorare prima di ottenere i tipi di argomento.

`count`\
[in] Numero di campi argomento da restituire (specifica anche le dimensioni della `ppFields` matrice).

`ppFields`\
[in, out] Matrice di campi che verranno compilati al ritorno di questo metodo.

`pFetched`\
[out] \( facoltativo) Numero di campi di tipo argomento effettivamente restituiti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il numero di tipi di argomento può essere ottenuto in anticipo con [GetTypeArgumentCount.](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)

## <a name="see-also"></a>Vedi anche
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
