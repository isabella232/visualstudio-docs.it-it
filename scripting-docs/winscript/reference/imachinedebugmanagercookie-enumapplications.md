---
title: IMachineDebugManagerCookie::EnumApplications | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09065e210e8919d149a221399aae854acc455bc0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087674"
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
Restituisce un enumeratore dell'elenco corrente delle applicazioni in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppeda`  
 [out] Enumeratore che contiene l'elenco corrente delle applicazioni in esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce un enumeratore dell'elenco corrente delle applicazioni in esecuzione. Il debugger IDE Usa questo metodo per visualizzare e collegare le applicazioni a fini di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)