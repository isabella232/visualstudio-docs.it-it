---
title: Proprietà IDebugProgramProvider2::GetProviderProcessData . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721836"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera un elenco di programmi in esecuzione da un processo specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parametri
`Flags`\
[in] Combinazione di flag dall'enumerazione [PROVIDER_FLAGS.](../../../extensibility/debugger/reference/provider-flags.md) I seguenti flag sono tipici per questa chiamata:

|Flag|Descrizione|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Il chiamante è in esecuzione su un computer remoto.|
|`PFLAG_DEBUGGEE`|È in corso il debug del chiamante (verranno restituite informazioni aggiuntive sul marshalling per ogni nodo).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Il chiamante è stato collegato ma non avviato dal debugger.|
|`PFLAG_GET_PROGRAM_NODES`|Il chiamante richiede la restituzione di un elenco di nodi di programma.|

`pPort`\
[in] Porta su cui è in esecuzione il processo chiamante.

`processId`\
[in] Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) contenente l'ID del processo che contiene il programma in questione.

`EngineFilter`\
[in] Matrice di GUID per i motori di debug assegnati per eseguire il debug di questo processo (questi verranno utilizzati per filtrare i programmi effettivamente restituiti in base al supporto dei motori forniti; se non vengono specificati motori, verranno restituiti tutti i programmi).

`pProcess`\
[fuori] Struttura [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) compilata con le informazioni richieste.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene in genere chiamato da un processo per ottenere un elenco di programmi in esecuzione in tale processo. Le informazioni restituite sono un elenco di [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetti.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
