---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 0b82ab6cd37f789e98ca08c635011a7e04f5b871
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835628"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Restituisce l'oggetto applicazione di debug associato a questo sito di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppda`  
 out Puntatore all'oggetto applicazione di debug associato al sito di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'host non supporta direttamente il debug.|  
  
## <a name="remarks"></a>Osservazioni  
 Il `GetApplication` metodo consente a un host intelligente di definire l'oggetto applicazione a cui appartiene ogni script. I motori di script devono tentare di chiamare questo metodo per ottenere l'applicazione contenitore e ricorrere a `IProcessDebugManager::GetDefaultApplication` se l'operazione ha esito negativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)