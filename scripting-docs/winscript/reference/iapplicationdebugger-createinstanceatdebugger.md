---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs
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
ms.openlocfilehash: 95489464128e706e755432bee991c5481f5af8bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425819"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Consente la creazione di oggetti nel processo del debugger dal codice che è out-of-process al debugger.  
  
> [!IMPORTANT]
> Questo metodo non deve essere implementato, perché consente codice non attendibile creare oggetti arbitrari in un thread debugger attendibile.  
  
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
  
 Il metodo non è attualmente implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)