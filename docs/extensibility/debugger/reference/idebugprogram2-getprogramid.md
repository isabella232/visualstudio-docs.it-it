---
description: Ottiene un GUID per questo programma.
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27793da2555f8bb1f61d0a9df6b616e2a551bf4813f1d416b71d7e3cd283d858
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276438"
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
[out] Restituisce `GUID` l'oggetto per questo programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un motore di debug deve restituire l'identificatore di programma originariamente passato ai [metodi OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) [o Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md) In questo modo è possibile identificare il programma tra i componenti del debugger.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
