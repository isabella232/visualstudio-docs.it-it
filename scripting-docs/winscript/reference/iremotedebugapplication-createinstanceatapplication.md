---
title: 'IRemoteDebugApplication:: CreateInstanceAtApplication | Microsoft Docs'
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
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572317"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Consente la creazione di oggetti nel processo dell'applicazione in base al codice out-of-process dell'applicazione.  
  
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
 in Identificatore di classe (CLSID) dell'oggetto da creare.  
  
 `pUnkOuter`  
 in Se `NULL`, l'oggetto non viene creato come parte di un'aggregazione. In caso contrario, `pUnkOuter` è un puntatore all'interfaccia `IUnknown` dell'oggetto aggregato (la `IUnknown` di controllo).  
  
 `dwClsContext`  
 in Contesto per l'esecuzione del codice eseguibile. I valori vengono ricavati dal `CLSCTX` di enumerazione.  
  
 `riid`  
 in Identificatore di interfaccia utilizzato per comunicare con l'oggetto.  
  
 `ppvObject`  
 out Indirizzo della variabile puntatore che riceve il puntatore a interfaccia richiesto in `riid`. Quando viene restituito correttamente, * `ppvObject` contiene il puntatore a interfaccia richiesto. In caso di errore, \* `ppvObject` contiene `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo delega per `CoCreateInstance`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)