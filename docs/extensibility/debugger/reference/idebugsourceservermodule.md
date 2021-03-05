---
description: Rappresenta le informazioni del server di origine contenute in un file PDB.
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74fa5f3aafea5f709777bbead81743c7c5aef358
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164643"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Rappresenta le informazioni del server di origine contenute in un file PDB.

## <a name="syntax"></a>Sintassi

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai motori del debugger e utilizzata dall'interfaccia utente del debugger.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugSourceServerModule` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matrice di informazioni sul server di origine.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
