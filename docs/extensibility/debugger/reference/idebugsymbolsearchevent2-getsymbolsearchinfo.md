---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718895"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Chiamato da un gestore eventi per recuperare i risultati relativi a un processo di caricamento dei simboli.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parametri
`pModule`\
[fuori] Oggetto IDebugModule3 che rappresenta il modulo per il quale sono stati caricati i simboli.

`pbstrDebugMessage`\
[in, out] Restituisce una stringa contenente eventuali messaggi di errore dal modulo. Se non viene visualizzato alcun errore, questa stringa conterrà solo il nome del modulo, ma non è mai vuota.

> [!NOTE]
> [C]: `pbstrDebugMessage` non `NULL` può essere e `SysFreeString`deve essere liberato con .

`pdwModuleInfoFlags`\
[fuori] Combinazione di flag dell'enumerazione [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) che indica se sono stati caricati simboli.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Quando un gestore riceve l'evento [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) dopo che viene effettuato un tentativo di caricare i simboli di debug per un modulo, il gestore può chiamare questometodo per determinare i risultati di tale caricamento.

## <a name="see-also"></a>Vedere anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
