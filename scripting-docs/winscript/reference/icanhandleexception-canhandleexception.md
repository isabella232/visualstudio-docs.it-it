---
title: 'ICanHandleException:: CanHandleException | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575713"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Determina se il chiamante del modulo di gestione di script è in grado di gestire un'eccezione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExcepInfo`  
 in Puntatore a una struttura `EXCEPINFO` contenente le informazioni che verranno segnalate se non viene trovato alcun gestore di eccezioni.  
  
 `pvar`  
 in Valore associato all'eccezione, ad esempio il valore generato da un'istruzione `throw`. Questo parametro può essere `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il chiamante può gestire l'eccezione|  
|`E_FAIL`|Il chiamante non è in grado di gestire l'eccezione.|  
  
## <a name="remarks"></a>Note  
 Se una chiamata a `IDispatchEx::InvokeEx`o a un metodo simile genera un'eccezione, il motore di script verifica la presenza di un chiamante nella catena di chiamante dello script che supporta l'interfaccia `ICanHandleException` e indica che è in grado di gestire l'eccezione. Se nessun chiamante è in grado di gestire l'eccezione, il motore di script si arresta.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)