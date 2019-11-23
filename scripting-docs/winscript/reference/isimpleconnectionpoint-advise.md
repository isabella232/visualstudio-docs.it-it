---
title: 'ISimpleConnectionPoint:: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571831"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Stabilisce una connessione tra l'oggetto punto di connessione semplice e il sink del client.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdisp`  
 in Puntatore all'interfaccia `IDispatch` sul sink di notifica del client. Il sink del client riceve le chiamate in uscita dal punto di connessione semplice.  
  
 `pdwCookie`  
 out Puntatore a un token restituito che identifica in modo univoco questa connessione. Il chiamante utilizza questo token in un secondo momento per eliminare la connessione passandola al metodo `ISimpleConnectionPoint::Unadvise`. Se la connessione non è stata stabilita correttamente, questo valore è zero.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo stabilisce una connessione tra l'oggetto punto di connessione semplice e il sink del client.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)