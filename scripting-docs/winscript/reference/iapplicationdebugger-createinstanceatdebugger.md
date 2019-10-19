---
title: 'IApplicationDebugger:: CreateInstanceAtDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577894"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Consente la creazione di oggetti nel processo del debugger tramite codice out-of-process nel debugger.  
  
> [!IMPORTANT]
> Questo metodo non deve essere implementato perché consente a codice non attendibile di creare oggetti arbitrari in un thread del debugger attendibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
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
  
 Il metodo non è attualmente implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)