---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728721"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Abilita un motore di debug che usa DCOM per richiedere all' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaccia utente di verificare che il firewall non blocchi il debug remoto.

## <a name="syntax"></a>Sintassi

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dall'oggetto porta della gestione debug della sessione.

## <a name="methods"></a>Metodi
 La tabella seguente illustra i metodi di `IDebugFirewallConfigurationCallback2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Richiede che il firewall non blocchi il debug remoto.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
