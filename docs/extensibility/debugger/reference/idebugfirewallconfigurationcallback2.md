---
description: Abilita un motore di debug che usa DCOM per richiedere all'interfaccia utente di Visual Studio di verificare che il firewall non blocchi il debug remoto.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c67cc1ab9335cfeb197ca67937510b3137d6432c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073612"
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
