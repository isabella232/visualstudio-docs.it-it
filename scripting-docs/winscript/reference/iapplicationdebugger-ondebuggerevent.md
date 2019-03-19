---
title: IApplicationDebugger::onDebuggerEvent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78bb3345463dfd682534dc60a216f3e0e8fdf2a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157776"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Gestisce l'evento dell'applicazione personalizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `riid`  
 [in] Identificatore di interfaccia per l'oggetto.  
  
 `punk`  
 [in] L'oggetto evento, che implementa l'interfaccia definita da `riid`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è attualmente implementato.|  
  
## <a name="remarks"></a>Note  
 La semantica di `IUnknown` è completamente definito dall'applicazione/debugger.  
  
 Questo metodo consente di estensioni personalizzate del modello del debugger. non è attualmente implementato.  
  
 Questo metodo viene chiamato quando `IDebugApplication::FireDebuggerEvent` viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)