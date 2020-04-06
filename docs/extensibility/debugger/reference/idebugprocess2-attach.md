---
title: Proprietà IDebugProcess2::Attach . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724189"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Collega il gestore di sessione di debug (SDM) al processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>Parametri
`pCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) utilizzato per la notifica dell'evento di debug.

`rgguidSpecificEngines`\
[in] Matrice di GUID di motori di debug da utilizzare per eseguire il debug di programmi in esecuzione nel processo. Questo parametro può essere un valore null. Per ulteriori informazioni, vedere Note.

`celtSpecificEngines`\
[in] Il numero di motori `rgguidSpecificEngines` di debug nella `rghrEngineAttach` matrice e la dimensione della matrice.

`rghrEngineAttach`\
[in, out] Matrice di codici HRESULT restituiti dai motori di debug. La dimensione di questa matrice `celtSpecificEngines` è specificata nel parametro. Ogni codice è `S_OK` `S_ATTACH_DEFERRED`in genere o . Quest'ultimo indica che il DE è attualmente collegato ad alcun programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati altri valori possibili.

|valore|Descrizione|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il processo specificato è già connesso al debugger.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione della sicurezza durante la procedura di collegamento.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Non è possibile connettere un processo desktop al debugger.|

## <a name="remarks"></a>Osservazioni
 La connessione a un processo collega il modello SDM a tutti i programmi in esecuzione in tale `rgguidSpecificEngines` processo di cui è possibile eseguire il debug dai motori di debug (DE) specificati nell'array. Impostare `rgguidSpecificEngines` il parametro su `GUID_NULL` un valore null o includerlo nella matrice da associare a tutti i programmi nel processo.

 Tutti gli eventi di debug che si verificano nel processo vengono inviati all'oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) specificato. Questo `IDebugEventCallback2` oggetto viene fornito quando il modello SDM chiama questo metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
