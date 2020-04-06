---
title: Proprietà IDebugWindowsComputerPort2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ef4162469651e4b69502d3a9639d1e86c62e0b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718222"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
Consente l'esecuzione di query per ottenere informazioni sul computer di destinazione.

## <a name="syntax"></a>Sintassi

```
IDebugWindowsComputerPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dagli oggetti porta del gestore di debug della sessione.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugWindowsComputerPort2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[Informazioni su GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera informazioni sul computer in cui è in esecuzione il debugger.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
