---
title: Proprietà IDebugCoreServer3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732816"
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
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia da un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia. Una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) può restituire anche questa interfaccia. Questa interfaccia viene utilizzata più spesso da un fornitore di porta personalizzato per avviare programmi su un server (locale o remoto).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi sul IDebugCoreServer2 interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[NomeServer GetServer](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera il nome del server.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versione descrittiva del nome del server|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica ai motori di debug specifici di connettersi automaticamente ai processi all'avvio di tali processi.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un codice di errore specifico quando il collegamento automatico ha esito negativo.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea un'istanza di un motore di debug nel server.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera un flag che indica se il server si trova sullo stesso computer del chiamante.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valore che indica il protocollo utilizzato per comunicare con il server.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Disabilita tutte le impostazioni di collegamento automatico per tutti i motori di debug di cui questo server è noto.|

## <a name="remarks"></a>Osservazioni
 Un fornitore di porta personalizzato riceve il [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia su una chiamata a [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md). L'interfaccia `IDebugCoreServer3` può essere ottenuta da tale interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
