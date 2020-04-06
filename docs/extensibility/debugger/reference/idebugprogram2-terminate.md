---
title: Metodo IDebugProgram2::Terminate . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722750"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Termina il programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Se possibile, il programma verrà terminato e scaricato dal processo; in caso contrario, il motore di debug (DE) eseguirà tutte le operazioni di pulizia necessarie.

 Questo metodo o il [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metodo viene chiamato dall'IDE, in genere in risposta all'utente interrompere tutto il debug. L'implementazione di questo metodo dovrebbe, idealmente, terminare il programma all'interno del processo. Se questo non è possibile, il DE dovrebbe impedire il programma di esecuzione più in questo processo (ed eseguire qualsiasi pulizia necessaria). Se `IDebugProcess2::Terminate` il metodo è stato chiamato dall'IDE, l'intero `IDebugProgram2::Terminate` processo verrà terminato dopo la chiamata al metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminare](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
