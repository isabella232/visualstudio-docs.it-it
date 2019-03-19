---
title: Interfaccia IRemoteDebugApplicationEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationEx Interface
ms.assetid: 8e16164d-dbb2-4488-9507-25ae34f343dc
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9e25a28ade1ac73b9e4837dae61e2d91f24c45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144407"
---
# <a name="iremotedebugapplicationex-interface"></a>Interfaccia IRemoteDebugApplicationEx
Rappresenta un'applicazione in esecuzione. Non dovrà corrispondere a un processo del sistema operativo. In genere, un debugger è destinato a un'applicazione per il debug. Il gestore di eseguire il Debug di processi in genere implementa l'oggetto applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IRemoteDebugApplicationEx` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplicationEx:GetHostPid](../../winscript/reference/iremotedebugapplicationex-gethostpid.md)|Restituisce l'ID di processo per l'applicazione host.|  
|GetHostMachineName|Restituisce il nome del computer in cui l'applicazione host è in esecuzione in.|  
|[IRemoteDebugApplicationEx:SetLocale](../../winscript/reference/iremotedebugapplicationex-setlocale.md)|Imposta la lingua per la localizzazione la debugger.|  
|[IRemoteDebugApplicationEx:ForceStepMode](../../winscript/reference/iremotedebugapplicationex-forcestepmode.md)|Forza il debugger in modalità di istruzione singola.|  
|[IRemoteDebugApplicationEx:RevokeBreak](../../winscript/reference/iremotedebugapplicationex-revokebreak.md)|Revoca un comando di interruzione.|  
|SetProxyBlanketAndAddRef|Aggiorna le informazioni di sicurezza COM su un proxy per un oggetto del debugger per garantire la compatibilità con il debug remoto da sistemi operativi basati su Windows 95.|  
|ReleaseFromSetProxyBlanket|AddRef rilasci da SetProxyBlanketAndAddRef.|