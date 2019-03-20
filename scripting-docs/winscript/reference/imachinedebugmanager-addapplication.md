---
title: IMachineDebugManager::AddApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96c1b865c722a3cceab331b81b1204ee682b911f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155615"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Aggiunge un'applicazione in esecuzione l'elenco delle applicazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pda`  
 [in] All'esecuzione applicazione elenco di applicazioni.  
  
 `pdwAppCookie`  
 [out] Un cookie utilizzato per rimuovere l'applicazione dalla gestione debug del computer.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal gestore di debug processo ogni volta che `IProcessDebugManager::AddApplication` viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IMachineDebugManager Interface](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)