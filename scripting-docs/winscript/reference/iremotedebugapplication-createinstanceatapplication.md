---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e17c5abcb21bfaad6de948c3676d29232da66cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944306"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Consente la creazione di oggetti nel processo dell'applicazione dal codice che è out-of-process per l'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rclsid`  
 [in] Identificatore (CLSID) dell'oggetto per creare la classe.  
  
 `pUnkOuter`  
 [in] Se `NULL`, l'oggetto non è viene creato come parte di un'aggregazione. In caso contrario, `pUnkOuter` è un puntatore all'oggetto aggregato `IUnknown` interfaccia (il controllo `IUnknown`).  
  
 `dwClsContext`  
 [in] Contesto per l'esecuzione di codice eseguibile. I valori sono ricavati dall'enumerazione `CLSCTX`.  
  
 `riid`  
 [in] L'identificatore di interfaccia utilizzato per comunicare con l'oggetto.  
  
 `ppvObject`  
 [out] Indirizzo della variabile puntatore che riceve il puntatore a interfaccia richiesto `riid`. Dopo la restituzione ha esito positivo, *`ppvObject` contiene il puntatore all'interfaccia richiesta. Nel caso di errore \* `ppvObject` contiene `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo delega al `CoCreateInstance`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)