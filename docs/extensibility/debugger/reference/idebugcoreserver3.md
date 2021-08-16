---
description: Questa interfaccia consente di accedere alle informazioni sul server in cui è in esecuzione il processo.
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7ab3323f7377f31e187dbb2642781ca54584b762d8c616ea9cba3eb37f50c3c5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377756"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Questa interfaccia consente di accedere alle informazioni sul server in cui è in esecuzione il processo.

## <a name="syntax"></a>Sintassi

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia da [un'interfaccia IDebugCoreServer2.](../../../extensibility/debugger/reference/idebugcoreserver2.md) Anche una chiamata [a GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) può restituire questa interfaccia. Questa interfaccia viene usata più spesso da un fornitore di porte personalizzato per avviare programmi in un server (locale o remoto).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi [nell'interfaccia IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera il nome del server.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versione descrittiva del nome del server|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica a motori di debug specifici di connettersi automaticamente ai processi all'avvio di tali processi.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un codice di errore specifico quando il collegamento automatico non riesce.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea un'istanza di un motore di debug nel server.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera un flag che indica se il server si trova nello stesso computer del chiamante.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valore che indica il protocollo utilizzato per comunicare con il server.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Disabilita tutte le impostazioni di collegamento automatico per tutti i motori di debug a cui questo server è a conoscenza.|

## <a name="remarks"></a>Commenti
 Un fornitore di porte personalizzato riceve [l'interfaccia IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) in una chiamata a [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3`L'interfaccia può essere ottenuta da tale interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
