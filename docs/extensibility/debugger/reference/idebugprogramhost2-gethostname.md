---
description: Ottiene il titolo, il nome descrittivo o il nome file del processo di hosting del programma.
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02583eca88274dc998d2fc85fce8cadc247e8e93
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634835"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Ottiene il titolo, il nome descrittivo o il nome file del processo di hosting del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>Parametri
`dwType`\
[in] Valore [dell'enumerazione GETHOSTNAME_TYPE.](../../../extensibility/debugger/reference/gethostname-type.md)

`pbstrHostName`\
[out] Restituisce il nome richiesto del processo di hosting.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 In un'implementazione tipica di questo metodo, il parametro viene ignorato e viene restituito un nome `dwType` descrittivo del computer host. Un'altra implementazione possibile è passare `dwType` il parametro a una chiamata al metodo [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) per ottenere il nome.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
