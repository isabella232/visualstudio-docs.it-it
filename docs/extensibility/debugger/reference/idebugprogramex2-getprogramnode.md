---
description: Ottiene il nodo di programma associato a un programma.
title: IDebugProgramEx2::GetProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 1545ffbf-1422-4b5d-9bb9-314ba8665041
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ddef19d4b8e889639c3f7d4deaccfbef0d676ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071548"
---
# <a name="idebugprogramex2getprogramnode"></a>IDebugProgramEx2::GetProgramNode
Ottiene il nodo di programma associato a un programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProgramNode( 
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProgramNode( 
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Parametri
`ppProgramNode`\
[out] Restituisce un [oggetto IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che rappresenta il nodo del programma associato a questo programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
