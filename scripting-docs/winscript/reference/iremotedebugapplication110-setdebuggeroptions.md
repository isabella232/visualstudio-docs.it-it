---
title: IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511d1f8b25aee4637455e3a5b8946f81f7410d65
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150829"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
Chiamato per aggiornare le opzioni del debugger. Questo metodo deve essere chiamato dopo [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md). Il [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) metodo reimposta automaticamente per le opzioni predefinite. Il valore predefinito di opzioni a 0 (SDO_NONE).  
  
> [!IMPORTANT]
>  [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>Parametri  
 `mask`  
 Il [enumerazione SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) maschera.  
  
 `value`  
 Il [enumerazione SCRIPT_DEBUGGER_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md) valore.  
  
## <a name="see-also"></a>Vedere anche  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interfaccia IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)