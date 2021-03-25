---
description: Alleghi una sessione a un programma.
title: 'IDebugProgramEx2:: alleghi | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4f7f6a083c37ece73be488ab0c4f6d4c25ce24c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084155"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Alleghi una sessione a un programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametri
`pCallback`\
in Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che rappresenta la funzione di callback a cui il motore di debug collegato invia gli eventi.

`dwReason`\
in Valore dell'enumerazione [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che descrive il motivo dell'operazione di connessione.

`pSession`\
in Valore che identifica in modo univoco la sessione che si connette al programma.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Questo metodo deve restituire `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se il programma è già collegato.

## <a name="remarks"></a>Commenti
 La porta che contiene il programma può usare il valore in `pSession` per determinare la sessione che sta tentando di connettersi al programma. Se, ad esempio, una porta consente la connessione di una sola sessione di debug a un processo alla volta, la porta può determinare se la stessa sessione è già collegata ad altri programmi nel processo.

> [!NOTE]
> L'interfaccia passata deve `pSession` essere considerata solo come un cookie, un valore che identifica in modo univoco il gestore di debug della sessione che si connette al programma; nessuno dei metodi nell'interfaccia fornita è funzionante.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
