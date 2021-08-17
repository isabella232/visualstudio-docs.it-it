---
description: Rappresenta le informazioni sul server di origine contenute in un file PDB.
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d8271fe7d639ab937f3b3a51ff66b86649b90693
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070897"
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
 Nella tabella seguente vengono illustrati i metodi di `IDebugSourceServerModule` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matrice di informazioni sul server di origine.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
