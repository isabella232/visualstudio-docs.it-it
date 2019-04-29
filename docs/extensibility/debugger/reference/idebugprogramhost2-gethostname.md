---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45919c6c9fafceecca2cb53fa9c2c9f43b68e382
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870006"
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

#### <a name="parameters"></a>Parametri
 `dwType`

 [in] Un valore compreso il [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumerazione.

 `pbstrHostName`

 [out] Restituisce il nome richiesto del processo di hosting.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 In una tipica implementazione di questo metodo, il `dwType` parametro viene ignorato e viene restituito un nome descrittivo della macchina host. Un altro possibile implementazione consiste nel passare il `dwType` parametro per una chiamata ai [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) metodo per ottenere il nome.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)