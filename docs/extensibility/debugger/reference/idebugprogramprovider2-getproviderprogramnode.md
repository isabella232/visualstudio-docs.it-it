---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c468745418c01b638cbc407342820b9127b460b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869815"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Recupera il nodo di programma per un programma specifico.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

#### <a name="parameters"></a>Parametri
 `Flags`

 [in] Una combinazione di flag dal [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumerazione. I flag seguenti sono più comuni per questa chiamata:

|Flag|Descrizione|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Chiamante è in esecuzione nel computer remoto.|
|`PFLAG_DEBUGGEE`|Chiamante è in corso il debug (verranno restituite informazioni aggiuntive sul marshalling per ogni nodo).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chiamante è stato collegato a ma non avviare dal debugger.|

 `pPort`

 [in] La porta del processo chiamante è in corso.

 `processId`

 [in] Un' [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che contiene l'ID del processo che contiene il programma in questione.

 `guidEngine`

 [in] GUID del motore di debug che il programma è associato (se presente).

 `programId`

 [in] ID del programma per cui ottenere il nodo di programma.

 `ppProgramNode`

 [out] Un' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto che rappresenta il nodo programma richiesto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)