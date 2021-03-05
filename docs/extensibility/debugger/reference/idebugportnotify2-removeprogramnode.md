---
description: Annulla la registrazione di un programma di cui è possibile eseguire il debug dalla porta in cui è in esecuzione.
title: 'IDebugPortNotify2:: RemoveProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::RemoveProgramNode
helpviewer_keywords:
- IDebugPortNotify2::RemoveProgramNode
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90918aed8652328a8aa02edac3517ec524a6cfa0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142648"
---
# <a name="idebugportnotify2removeprogramnode"></a>IDebugPortNotify2::RemoveProgramNode
Annulla la registrazione di un programma di cui è possibile eseguire il debug dalla porta in cui è in esecuzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT RemoveProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int RemoveProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parametri
`pProgramNode`\
in Un Esplora [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresenta il programma di cui annullare la registrazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo rimuove un nodo di programma che è stato aggiunto con una chiamata al metodo [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
