---
description: Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito ed estende IDebugComPlusSymbolProvider.
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3a29fcc5cca12698919f0bc4af02bc3db1fe3fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163317"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Rappresenta un provider di simboli COM+ con metodi specifici del codice gestito ed estende il IDebugComPlusSymbolProvider **IDebugComPlusSymbolProvider**[](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md).

## <a name="syntax"></a>Sintassi

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Determina se il metodo specificato dispone di informazioni sulla riga.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Recupera un tipo in base al nome.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Recupera un tipo in base al relativo token.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Determina se l'indirizzo di debug specificato è un punto di sequenza.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Carica i simboli di debug utilizzando il metodo di callback specificato.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Caricare i simboli di debug da un flusso di dati dato l'oggetto **ICorDebugModule** .|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Carica i simboli di debug in base all'oggetto **ICorDebugModule** .|

## <a name="requirements"></a>Requisiti
 Intestazione: sh. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
