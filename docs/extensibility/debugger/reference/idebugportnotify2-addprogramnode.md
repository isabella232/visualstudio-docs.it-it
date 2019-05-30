---
title: IDebugPortNotify2::AddProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::AddProgramNode
helpviewer_keywords:
- IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0afd0b2ae50555e29a75159edb8f52635730a56
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319471"
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
Registra un programma che è possibile eseguire il debug con la porta in cui viene eseguito.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT AddProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int AddProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parametri
`pProgramNode`\
[in] Un' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto che rappresenta il programma da registrare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Un programma nodo può essere annullata la registrazione dalla porta chiamando il [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)