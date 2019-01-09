---
title: ICanHandleException::CanHandleException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 784463f9e465aac005f5454be28a0043069dcb69
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089999"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Determina se il chiamante del motore di script può gestire un'eccezione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExcepInfo`  
 [in] Puntatore a un `EXCEPINFO` struttura che contiene le informazioni che verranno segnalate se non viene trovato alcun gestore di eccezioni.  
  
 `pvar`  
 [in] Un valore associato all'eccezione, ad esempio il valore generato da un `throw` istruzione. Questo parametro può essere `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il chiamante può gestire l'eccezione|  
|`E_FAIL`|Il chiamante non è possibile gestire l'eccezione.|  
  
## <a name="remarks"></a>Note  
 Se una chiamata a `IDispatchEx::InvokeEx`, o un metodo simile, genera un'eccezione, il motore di script controlla per dei chiamanti nella catena di chiamante dello script che supporta il `ICanHandleException` l'interfaccia e indica che è possibile gestire l'eccezione. Se nessun chiamante può gestire l'eccezione, il motore di script si interrompe.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)