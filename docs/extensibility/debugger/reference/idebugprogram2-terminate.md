---
description: Termina il programma.
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 880bf4e727d90c19cf11f42cc3020124235bb1e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171983"
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

## <a name="remarks"></a>Commenti
 Se possibile, il programma verrà terminato e scaricato dal processo; in caso contrario, il motore di debug (DE) eseguirà tutte le operazioni di pulizia necessarie.

 Questo metodo o il metodo [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) viene chiamato dall'IDE, in genere in risposta all'interruzione di tutto il debug da parte dell'utente. L'implementazione di questo metodo dovrebbe, idealmente, terminare il programma nel processo. Se ciò non è possibile, il DE deve impedire che il programma esegua altre operazioni in questo processo (ed eseguire le operazioni di pulizia necessarie). Se il `IDebugProcess2::Terminate` metodo è stato chiamato dall'IDE, l'intero processo verrà terminato in un secondo momento dopo la `IDebugProgram2::Terminate` chiamata del metodo.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md).
