---
title: 'IDebugProgramNode2: etachDebugger_V7:D | Microsoft Docs'
description: Questo metodo è una forma obsoleta obsoleta del metodo di scollegamento utilizzato prima di Visual Studio 2005.
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16630be49dd884f8bcc82da2fead158eb3a25e5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053555"
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
> A partire da Visual Studio 2005, questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL` .

Questo metodo viene chiamato quando il debugger si chiude in modo imprevisto. Quando viene chiamato questo metodo, il DE deve riprendere il programma come se l'utente fosse scollegato da esso. Non devono essere inviati altri eventi di debug. Il programma deve trovarsi in uno stato in cui può essere collegato da un'altra istanza del debugger.

## <a name="see-also"></a>Vedi anche

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
