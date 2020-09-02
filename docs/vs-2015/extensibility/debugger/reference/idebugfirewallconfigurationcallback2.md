---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 04d64ac489858e3a912b144b494430aec5b925d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197043"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Abilita un motore di debug che usa DCOM per richiedere all' [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfaccia utente di verificare che il firewall non blocchi il debug remoto.  
  
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
