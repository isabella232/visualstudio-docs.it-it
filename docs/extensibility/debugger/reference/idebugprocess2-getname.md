---
description: Ottiene il titolo, il nome descrittivo o il nome file del processo.
title: IDebugProcess2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 920db4fbd7702b0a01997dee1570128d6d38285a35f0893985e6480fa72b25ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416313"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
Ottiene il titolo, il nome descrittivo o il nome file del processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName( 
   GETNAME_TYPE  gnType,
   BSTR*         pbstrName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE  gnType,
   out string         pbstrName
);
```

## <a name="parameters"></a>Parametri
`gnType`\
[in] Valore [dell'enumerazione GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) che specifica il tipo di nome da restituire.

`pbstrName`\
[out] Restituisce il nome del processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
