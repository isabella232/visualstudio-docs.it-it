---
description: Ottiene un GUID per il programma.
title: 'IDebugProgram2:: GetProgramId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45721d4214c396f3366bd23c2bc48e74a1427ec8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168963"
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
out Restituisce l'oggetto `GUID` per questo programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un motore di debug (de) deve restituire l'identificatore del programma passato originariamente ai metodi [alleghi](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) o [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md) . In questo modo è possibile identificare il programma tra i componenti del debugger.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
