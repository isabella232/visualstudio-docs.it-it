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
ms.openlocfilehash: b43d6c3edde39b137116dc5215745f066207e25d00c75e8a1dc351e8c1ccefc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433216"
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
