---
title: IProcessDebugManager::GetDefaultApplication | Microsoft Docs
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
ms.openlocfilehash: 6fec84a60863b426f2f65c26e2375262b109d635
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953972"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Restituisce un oggetto di applicazione predefinito per il processo corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDefaultApplication(  
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
 Questo metodo crea un nuovo oggetto di applicazione di debug e lo aggiunge all'esecuzione elenco di applicazioni, se necessario.  
  
 Motori di linguaggio devono usare l'applicazione specificata dal `GetDefaultApplication` metodo se sono in esecuzione in un host che non fornisce un'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)