---
description: Questa interfaccia fornisce diversi metodi per accedere al server e alle funzionalità di notifica di una porta.
title: Interfaccia IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a606358b708b49f866063eeefc25b4e0c3fec44cab9fa8689492a475faeb3749
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417496"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Questa interfaccia fornisce diversi metodi per accedere al server e alle funzionalità di notifica di una porta.

## <a name="syntax"></a>Sintassi

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porte personalizzato può implementare questa interfaccia anche se gestisce il debug remoto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un argomento per i metodi [nell'interfaccia IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) fornisce questa interfaccia. Anche [la chiamata di QueryInterface](/cpp/atl/queryinterface) su [un'interfaccia IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) può ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi definiti in [IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md)questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica della porta da questa porta.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia per il server che ospita questa porta.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|

## <a name="remarks"></a>Commenti
 Il nome " `IDebugDefaultPort2` " è un po' erre, perché non rappresenta una porta predefinita. Potrebbe essere chiamato "IDebugPort3".

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
