---
description: Recupera un elenco di programmi in esecuzione da un processo specificato.
title: Interfaccia IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 258a8c3309e695258c1599101e2b8fdc44e4f735
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126375"
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
[in] Combinazione di flag [dell'enumerazione PROVIDER_FLAGS.](../../../extensibility/debugger/reference/provider-flags.md) I flag seguenti sono tipici di questa chiamata:

|Flag|Descrizione|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Il chiamante è in esecuzione nel computer remoto.|
|`PFLAG_DEBUGGEE`|È in corso il debug del chiamante. Verranno restituite informazioni aggiuntive sul marshalling per ogni nodo.|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Il chiamante è stato collegato a ma non avviato dal debugger.|
|`PFLAG_GET_PROGRAM_NODES`|Il chiamante richiede la visualizzazione di un elenco di nodi di programma da restituire.|

`pPort`\
[in] Porta su cui è in esecuzione il processo chiamante.

`processId`\
[in] Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) contenente l'ID del processo che contiene il programma in questione.

`EngineFilter`\
[in] Matrice di GUID per i motori di debug assegnati per eseguire il debug di questo processo( che verranno usati per filtrare i programmi effettivamente restituiti in base al supporto dei motori forniti; se non viene specificato alcun motore, verranno restituiti tutti i programmi).

`pProcess`\
[out] Struttura [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) che viene compilata con le informazioni richieste.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene in genere chiamato da un processo per ottenere un elenco di programmi in esecuzione in tale processo. Le informazioni restituite sono un elenco di [oggetti IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>Vedi anche
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
