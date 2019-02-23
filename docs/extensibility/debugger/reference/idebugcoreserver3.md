---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 629e35e8756be1dfa6df9f21eda02624b4c363de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691319"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Questa interfaccia fornisce accesso alle informazioni sul server che in cui viene eseguito il processo.

## <a name="syntax"></a>Sintassi

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Visual Studio implementa questa interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Uso [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia da un' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia. Una chiamata a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) può restituire anche questa interfaccia. Questa interfaccia viene utilizzata in genere da un fornitore di porte personalizzate per avviare i programmi in un server (locale o remoto).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi nel [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera il nome del server.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versione breve del nome del server|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica i motori di debug specifiche connettersi automaticamente ai processi quando avvia i processi.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un codice di errore specifico quando automatico collegamento ha esito negativo.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea un'istanza di un motore di debug nel server.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera un flag che indica se il server è nello stesso computer del chiamante.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valore che indica il protocollo usato per comunicare con il server.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Disabilita tutte le connessione automatica le impostazioni per tutti i motori di debug, che questo server è a conoscenza.|

## <a name="remarks"></a>Note
 Un fornitore di porte personalizzato riceve la [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia in una chiamata a [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). Il `IDebugCoreServer3` interfaccia può essere ottenuta da tale interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)