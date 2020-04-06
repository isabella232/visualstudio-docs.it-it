---
title: IDebugBeforeSymbolSearchEvent2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736106"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di sessione di debug (SDM) per impostare il messaggio della barra di stato durante i caricamenti di simboli.

## <a name="syntax"></a>Sintassi

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il DE implementa questa interfaccia quando è necessario impostare il messaggio della barra di stato durante il caricamento di simboli. Questa interfaccia viene implementata solo dai motori di debug che funzionano con o fanno parte degli interpreti di script. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata sullo stesso oggetto di questa interfaccia (il modello SDM utilizza **QueryInterface** per accedere il **IDebugEvent2** interfaccia).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il DE crea e invia questo oggetto evento quando è necessario impostare il messaggio della barra di stato durante il caricamento di simboli. L'evento viene inviato utilizzando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita dal modello SDM quando è collegato al programma in fase di debug.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugBeforeSymbolSearchEvent2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera il nome del modulo attualmente sottoposto a debug.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
