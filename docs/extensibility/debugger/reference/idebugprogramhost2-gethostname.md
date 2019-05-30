---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 851905a9ca642f029444a2f6c1adfdfe543fdf70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351277"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Ottiene il titolo, un nome descrittivo o un nome file del processo di hosting di questo programma.

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
[in] Un valore compreso il [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumerazione.

`pbstrHostName`\
[out] Restituisce il nome richiesto del processo di hosting.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 In una tipica implementazione di questo metodo, il `dwType` parametro viene ignorato e viene restituito un nome descrittivo della macchina host. Un altro possibile implementazione consiste nel passare il `dwType` parametro per una chiamata ai [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) metodo per ottenere il nome.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)