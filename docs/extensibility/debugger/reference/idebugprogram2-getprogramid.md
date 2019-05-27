---
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca86175d34cc1bfd54882adda7e1f7cb464fb22f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212639"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ottiene un GUID per il programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parametri
`pguidProgramId`\
[out] Restituisce il `GUID` per questo programma.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Un motore di debug (DE) deve restituire l'identificatore di programma passato in origine per il [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) oppure [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodi. In questo modo identificazione del programma in debugger componenti.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)