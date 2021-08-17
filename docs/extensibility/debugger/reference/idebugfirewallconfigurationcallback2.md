---
description: Abilita un motore di debug che usa DCOM per chiedere all'interfaccia Visual Studio per assicurarsi che il firewall non blocchi il debug remoto.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 18dd45fa041732f733d121d7304650ea82cf5983a76fa58e434b088ba8fcb684
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402766"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Abilita un motore di debug che usa DCOM per chiedere all'interfaccia utente di assicurarsi che [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] il firewall non blocchi il debug remoto.

## <a name="syntax"></a>Sintassi

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Implementato dall'oggetto porta della gestione del debug della sessione.

## <a name="methods"></a>Metodi
 Nella tabella seguente vengono illustrati i metodi di `IDebugFirewallConfigurationCallback2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Richiede che il firewall non blocchi il debug remoto.|

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
