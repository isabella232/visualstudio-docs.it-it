---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb185e098d76184d3a74df380eb8a5e66bc699df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869960"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Il motore di debug (DE) Invia questa interfaccia a gestione debug sessione (SDM) per impostare il messaggio della barra di stato durante i caricamenti dei simboli.

## <a name="syntax"></a>Sintassi

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia quando deve impostare il messaggio della barra di stato durante i caricamenti dei simboli. Questa interfaccia viene implementata solo dai motori di debug che funzionano con o fanno parte di interpreti di script. L'interfaccia [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (il SDM USA **QueryInterface** per accedere all'interfaccia **IDebugEvent2** ).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento quando deve impostare il messaggio della barra di stato durante i caricamenti dei simboli. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegata al programma di cui è in corso il debug.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugBeforeSymbolSearchEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera il nome del modulo di cui è in corso il debug.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
