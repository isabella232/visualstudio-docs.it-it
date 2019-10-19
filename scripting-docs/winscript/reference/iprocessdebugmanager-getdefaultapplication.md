---
title: 'IProcessDebugManager:: GetDefaultApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576802"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Restituisce un oggetto applicazione predefinito per il processo corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppda`  
 out Oggetto applicazione di debug per l'applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un nuovo oggetto applicazione di debug e lo aggiunge all'elenco di applicazioni in esecuzione, se necessario.  
  
 I motori di linguaggio devono usare l'applicazione specificata dal metodo `GetDefaultApplication` se sono in esecuzione in un host che non fornisce un'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)