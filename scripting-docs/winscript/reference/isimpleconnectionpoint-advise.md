---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
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
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153110"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Stabilisce una connessione tra l'oggetto punto di connessione semplici e il sink del client.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdisp`  
 [in] Puntatore al `IDispatch` sink di notifica del interfaccia sul client. Sink del client riceve le chiamate in uscita dal punto di connessione semplici.  
  
 `pdwCookie`  
 [out] Puntatore a un token restituito che identifica questa connessione. Il chiamante utilizza questo token in un secondo momento per eliminare la connessione passando al `ISimpleConnectionPoint::Unadvise` (metodo). Se la connessione non è stata stabilita correttamente, questo valore è zero.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di stabilire una connessione tra l'oggetto punto di connessione semplice e un sink del client.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)