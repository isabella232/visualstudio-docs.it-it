---
description: Consente di eseguire query per ottenere informazioni sul computer di destinazione.
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c7e940c2284b5b39097226f9a5b0c3b34a0d18
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222952"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Consente di eseguire query per ottenere informazioni sul computer di destinazione.

## <a name="syntax"></a>Sintassi

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dagli oggetti Port della gestione debug della sessione.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugWindowsComputerPort2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera le informazioni sul computer in cui è in esecuzione il debugger.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
