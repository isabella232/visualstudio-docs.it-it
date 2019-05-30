---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed38c530ee972e413ee98cc9d94f0f19a9b57069
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351711"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Questa interfaccia fornisce diversi metodi per l'accesso ai server di una porta e le funzionalità di notifica.

## <a name="syntax"></a>Sintassi

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porte personalizzato possa anche implementare questa interfaccia se gestisce il debug remoto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Argomento di metodi sul [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia fornisce questa interfaccia. La chiamata [QueryInterface](/cpp/atl/queryinterface) in un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia possa anche ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi definiti nel [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica di porta da questa porta.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia per il server che ospita questa porta.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se questa porta è in esecuzione nel computer locale.|

## <a name="remarks"></a>Note
 Il nome "`IDebugDefaultPort2`" è un po' impropria poiché non rappresenta una porta predefinita. È possibile chiamare "IDebugPort3."

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)