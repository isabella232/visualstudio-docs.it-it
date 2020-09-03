---
title: 'IDebugProgram2:: terminate | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
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

 Questo metodo o il metodo [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) viene chiamato dall'IDE, in genere in risposta all'interruzione di tutto il debug da parte dell'utente. L'implementazione di questo metodo dovrebbe, idealmente, terminare il programma nel processo. Se ciò non è possibile, il DE deve impedire che il programma esegua altre operazioni in questo processo (ed eseguire le operazioni di pulizia necessarie). Se il `IDebugProcess2::Terminate` metodo è stato chiamato dall'IDE, l'intero processo verrà terminato in un secondo momento dopo la `IDebugProgram2::Terminate` chiamata del metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md).
