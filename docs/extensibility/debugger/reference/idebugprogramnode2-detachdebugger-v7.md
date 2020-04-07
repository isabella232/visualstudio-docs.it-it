---
title: IDebugProgramNode2::DetachDebugger_V7 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722116"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Deprecato. NON UTILIZZARE.

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

Un'implementazione `E_NOTIMPL`deve sempre restituire .

## <a name="remarks"></a>Osservazioni

> [!WARNING]
> A partire da Visual Studio 2005, questo metodo `E_NOTIMPL`non viene più utilizzato e deve sempre restituire .

Questo metodo viene chiamato quando il debugger si chiude in modo imprevisto. Quando questo metodo viene chiamato, il DE deve riprendere il programma come se l'utente si è disconnesso da esso. Non devono essere inviati altri eventi di debug. Il programma deve trovarsi in uno stato in cui è collegabile da un'altra istanza del debugger.

## <a name="see-also"></a>Vedere anche

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
