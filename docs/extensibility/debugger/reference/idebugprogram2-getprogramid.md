---
title: IDebugProgram2::GetProgramId . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb172f48b63ef2ec182f1a83d599a91eff1e2ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722769"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Ottiene un GUID per questo programma.

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
[fuori] Restituisce `GUID` l'oggetto per questo programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Un motore di debug (DE) deve restituire l'identificatore di programma originariamente passato ai metodi [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) o [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md) Ciò consente l'identificazione del programma tra i componenti del debugger.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
