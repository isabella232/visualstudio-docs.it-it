---
description: Il motore di debug (DE) invia questa interfaccia al gestore di debug sessione (SDM) per impostare il messaggio della barra di stato durante il caricamento dei simboli.
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5e3cd48bef3c23e69208f1741cacb8adad907ede
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627522"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di debug sessione (SDM) per impostare il messaggio della barra di stato durante il caricamento dei simboli.

## <a name="syntax"></a>Sintassi

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il de implementa questa interfaccia quando deve impostare il messaggio della barra di stato durante il caricamento del simbolo. Questa interfaccia viene implementata solo dai motori di debug che funzionano con o fanno parte degli interpreti di script. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia (SDM usa **QueryInterface** per accedere all'interfaccia **IDebugEvent2).**

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento quando deve impostare il messaggio della barra di stato durante il caricamento del simbolo. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugBeforeSymbolSearchEvent2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Recupera il nome del modulo attualmente in fase di debug.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
