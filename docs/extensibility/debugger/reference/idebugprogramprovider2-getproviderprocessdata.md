---
description: Recupera un elenco di programmi in esecuzione da un processo specificato.
title: 'IDebugProgramProvider2:: GetProviderProcessData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b878a6731a9a7f2bf58bf55530d0b5f83cc978de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151558"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera un elenco di programmi in esecuzione da un processo specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parametri
`Flags`\
in Combinazione di flag dell'enumerazione [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Per questa chiamata sono tipici i flag seguenti:

|Flag|Descrizione|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Il chiamante è in esecuzione nel computer remoto.|
|`PFLAG_DEBUGGEE`|Il chiamante è attualmente in fase di debug. verranno restituite informazioni aggiuntive sul marshalling per ogni nodo.|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Il chiamante è stato associato a ma non avviato dal debugger.|
|`PFLAG_GET_PROGRAM_NODES`|Il chiamante chiede un elenco di nodi del programma da restituire.|

`pPort`\
in Porta su cui è in esecuzione il processo chiamante.

`processId`\
in Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) che contiene l'ID del processo che contiene il programma in questione.

`EngineFilter`\
in Matrice di GUID per i motori di debug assegnati per eseguire il debug del processo. questi verranno utilizzati per filtrare i programmi effettivamente restituiti in base al supporto dei motori forniti. se non viene specificato alcun motore, verranno restituiti tutti i programmi.

`pProcess`\
out Struttura [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) compilata con le informazioni richieste.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene in genere chiamato da un processo per ottenere un elenco di programmi in esecuzione in tale processo. Le informazioni restituite sono un elenco di oggetti [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
