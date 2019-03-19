---
title: IRemoteDebugApplication::DisconnectDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.DisconnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::DisconnectDebugger
ms.assetid: 989e5a34-0267-4a2e-96b6-e1dcc2ffe883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ff016752116664ca2c2cf71a7676fcb6a14ab61
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151076"
---
# <a name="iremotedebugapplicationdisconnectdebugger"></a>IRemoteDebugApplication::DisconnectDebugger
Consente di disconnettere il debugger corrente dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT DisconnectDebugger();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di disconnettere il debugger corrente dall'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)