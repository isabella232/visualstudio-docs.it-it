---
description: Collegare una sessione a un programma.
title: IDebugProgramEx2::Attach | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c97b8711f788c35c4e586c43f9c95c384076831a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071580"
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
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che rappresenta la funzione di callback a cui il motore di debug collegato invia gli eventi.

`dwReason`\
[in] Valore dell'enumerazione [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) che descrive il motivo dell'operazione di collegamento.

`pSession`\
[in] Valore che identifica in modo univoco la sessione collegata al programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, `S_OK` restituisce ; in caso contrario, restituisce un codice di errore. Questo metodo deve restituire `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se il programma è già collegato.

## <a name="remarks"></a>Commenti
 La porta che contiene il programma può utilizzare il valore in per determinare quale sessione sta `pSession` tentando di connettersi al programma. Ad esempio, se una porta consente a una sola sessione di debug di connettersi a un processo alla volta, la porta può determinare se la stessa sessione è già collegata ad altri programmi nel processo.

> [!NOTE]
> L'interfaccia passata deve essere considerata solo come un cookie, un valore che identifica in modo univoco la gestione del debug di sessione che si collega a questo programma. Nessuno dei metodi nell'interfaccia fornita è `pSession` funzionale.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
