---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70dd250359d52ae0929fb5fb2c60087f66af2160
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095121"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa l'host su un errore in fase di esecuzione di script durante il processo di Debug di gestione non trova un debugger di script Just In Time.  
  
 Per implementare un debugger nell'host, si consiglia di gestire [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Basato su un'azione dell'utente, l'host può collegare il debugger e tornare, o restituire l'avvio del debugger nel OnScriptErrorDebug `pfEnterDebugger` parametro. È anche necessario implementare questa interfaccia per ricevere le notifiche relative all'errore di runtime, anche se non sono presenti alcun debugger esterno che può essere interpretato dal gestore di eseguire il Debug del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pErrorDebug`  
 [in] Errore in fase di esecuzione che si è verificato.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Se si desidera chiamare [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) se l'utente decide di continuare senza debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 È anche consigliabile implementare questa interfaccia per ricevere una notifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)