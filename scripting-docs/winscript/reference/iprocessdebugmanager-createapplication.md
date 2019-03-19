---
title: IProcessDebugManager::CreateApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateApplication
ms.assetid: d6b646f2-8af0-445c-ae7e-a9772042b3a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d7f2246b327393a810170f5b133f2885186c3a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152824"
---
# <a name="iprocessdebugmanagercreateapplication"></a>IProcessDebugManager::CreateApplication
Crea un nuovo oggetto di applicazione di debug per questa applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppda`  
 [out] L'oggetto di applicazione di debug per questa applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'oggetto creato da questo metodo non ha un nome e non viene aggiunto all'esecuzione elenco delle applicazioni. Usare il `IProcessDebugManager::AddApplication` per aggiungere l'applicazione di debug per l'elenco di applicazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)