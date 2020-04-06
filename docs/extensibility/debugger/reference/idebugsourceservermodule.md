---
title: Proprietà IDebugSourceServerModule . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719917"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Rappresenta le informazioni sul server di origine contenute in un file PDB.

## <a name="syntax"></a>Sintassi

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dai motori del debugger e utilizzata dall'interfaccia utente del debugger.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono `IDebugSourceServerModule`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matrice di informazioni sul server di origine.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
