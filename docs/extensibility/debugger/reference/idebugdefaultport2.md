---
description: Questa interfaccia offre diversi metodi per l'accesso alle funzionalità server e di notifica di una porta.
title: IDebugDefaultPort2 | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 03eb9f8c1bae74f15d295a72b27821d41b8282a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067114"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Questa interfaccia offre diversi metodi per l'accesso alle funzionalità server e di notifica di una porta.

## <a name="syntax"></a>Sintassi

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia per rappresentare la porta di debug per l'accesso ai programmi. Un fornitore di porte personalizzato può inoltre implementare questa interfaccia se gestisce il debug remoto.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un argomento dei metodi nell'interfaccia [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) fornisce questa interfaccia. Questa interfaccia può essere ottenuta anche chiamando [QueryInterface](/cpp/atl/queryinterface) su un'interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
 Oltre ai metodi definiti in [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ottiene l'interfaccia di notifica della porta da questa porta.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ottiene l'interfaccia al server che ospita questa porta.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se la porta è in esecuzione nel computer locale.|

## <a name="remarks"></a>Commenti
 Il nome " `IDebugDefaultPort2` " è un bit di un nome non appropriato, perché non rappresenta una porta predefinita. Potrebbe essere chiamato "IDebugPort3".

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
