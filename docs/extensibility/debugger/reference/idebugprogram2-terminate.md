---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b80afe3f0061e016301b86229f2eacedf217a43
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709304"
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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se possibile, verrà terminato e scaricato dal processo; il programma in caso contrario, il motore di debug (DE) eseguirà le operazioni di pulitura necessarie.

 Questo metodo o la [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) viene chiamato dall'IDE, in genere in risposta all'utente di interrompere il debug di tutti. L'implementazione di questo metodo deve, in teoria, terminare il programma all'interno del processo. In caso contrario, la Germania deve impedire che il programma in esecuzione altri in questo processo ed eseguire la pulizia necessaria. Se il `IDebugProcess2::Terminate` metodo è stato chiamato dall'IDE, l'intero processo verrà terminato un certo momento dopo la `IDebugProgram2::Terminate` viene chiamato il metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)