---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 29cbcebc5bdc51be4223b2592bbe6ac3ae76525d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086359"
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