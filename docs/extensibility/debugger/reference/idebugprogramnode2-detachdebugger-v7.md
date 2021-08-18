---
title: IDebugProgramNode2::D etachDebugger_V7 | Microsoft Docs
description: Questo metodo è una forma obsoleta e deprecata del metodo detach usato prima Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47ad13cc0f3f01665535e6b9d8168af79eb299f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029983"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Deprecato. NON USARE.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Valore restituito

Un'implementazione deve sempre restituire `E_NOTIMPL` .

## <a name="remarks"></a>Commenti

> [!WARNING]
> A Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL` .

Questo metodo viene chiamato quando il debugger si chiude in modo imprevisto. Quando questo metodo viene chiamato, deretieni il programma come se l'utente si scollegava da esso. Non è necessario inviare altri eventi di debug. Il programma deve essere in uno stato in cui è collegabile da un'altra istanza del debugger.

## <a name="see-also"></a>Vedi anche

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
