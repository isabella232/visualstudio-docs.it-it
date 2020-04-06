---
title: Proprietà IDebugProgramEx2::Attach . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722385"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Collegare una sessione a un programma.

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
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che rappresenta la funzione di callback a cui il motore di debug associato invia eventi.

`dwReason`\
[in] Valore dell'enumerazione [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che descrive il motivo dell'operazione di collegamento.

`pSession`\
[in] Valore che identifica in modo univoco la sessione che si sta collegando al programma.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce un codice di errore. Questo metodo `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` deve restituire se il programma è già collegato.

## <a name="remarks"></a>Osservazioni
 La porta che contiene il programma `pSession` può utilizzare il valore in per determinare quale sessione sta tentando di connettersi al programma. Ad esempio, se una porta consente la connessione a un processo a una sola sessione di debug alla volta, la porta può determinare se la stessa sessione è già collegata ad altri programmi nel processo.

> [!NOTE]
> L'interfaccia `pSession` passata deve essere trattata solo come un cookie, un valore che identifica in modo univoco il gestore di debug della sessione che si collega a questo programma; nessuno dei metodi sull'interfaccia fornita è funzionale.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
