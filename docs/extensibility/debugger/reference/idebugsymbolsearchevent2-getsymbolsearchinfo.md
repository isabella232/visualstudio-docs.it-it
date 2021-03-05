---
description: Chiamato da un gestore eventi per recuperare i risultati relativi a un processo di caricamento dei simboli.
title: 'IDebugSymbolSearchEvent2:: GetSymbolSearchInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f03562f3370268f720b2d8053bbd6a2979f6a19
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145768"
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
out Oggetto IDebugModule3 che rappresenta il modulo per il quale sono stati caricati i simboli.

`pbstrDebugMessage`\
[in, out] Restituisce una stringa contenente tutti i messaggi di errore del modulo. Se non si verificano errori, questa stringa conterrà solo il nome del modulo, ma non sarà mai vuota.

> [!NOTE]
> [C++] `pbstrDebugMessage` non può essere `NULL` e deve essere liberato con `SysFreeString` .

`pdwModuleInfoFlags`\
out Combinazione di flag dell'enumerazione [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) che indica se sono stati caricati simboli.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Quando un gestore riceve l'evento [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) dopo aver eseguito un tentativo di caricare i simboli di debug per un modulo, il gestore può chiamare questo metodo per determinare i risultati del caricamento.

## <a name="see-also"></a>Vedi anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
