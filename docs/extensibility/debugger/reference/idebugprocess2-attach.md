---
description: Collega la gestione del debug di sessione (SDM) al processo.
title: Interfaccia IDebugProcess2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82251c831b1649d65939079244291d93eddb85d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057660"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Collega la gestione del debug di sessione (SDM) al processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametri
`pCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) usato per la notifica degli eventi di debug.

`rgguidSpecificEngines`\
[in] Matrice di GUID dei motori di debug da utilizzare per eseguire il debug di programmi in esecuzione nel processo. Questo parametro può essere un valore Null. Per ulteriori informazioni, vedere Note.

`celtSpecificEngines`\
[in] Numero di motori di debug nella `rgguidSpecificEngines` matrice e dimensioni della `rghrEngineAttach` matrice.

`rghrEngineAttach`\
[in, out] Matrice di codici HRESULT restituiti dai motori di debug. Le dimensioni di questa matrice vengono specificate nel `celtSpecificEngines` parametro . Ogni codice è in genere `S_OK` o `S_ATTACH_DEFERRED` . Quest'ultimo indica che de è attualmente collegato a nessun programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati altri valori possibili.

|Valore|Descrizione|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il processo specificato è già collegato al debugger.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione di sicurezza durante la procedura di collegamento.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processo desktop non può essere collegato al debugger.|

## <a name="remarks"></a>Commenti
 La connessione a un processo collega SDM a tutti i programmi in esecuzione in tale processo di cui i motori di debug (DE) possono eseguire il debug specificati nella `rgguidSpecificEngines` matrice . Impostare il `rgguidSpecificEngines` parametro su un valore Null o includere nella matrice da collegare a tutti i programmi nel `GUID_NULL` processo.

 Tutti gli eventi di debug che si verificano nel processo vengono inviati [all'oggetto IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) specificato. Questo `IDebugEventCallback2` oggetto viene fornito quando SDM chiama questo metodo.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
