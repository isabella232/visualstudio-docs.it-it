---
title: 'IActiveScriptSiteDebugEx:: OnCanNotJITScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572186"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa l'host sull'errore di run-time di uno script quando Gestione debug processo non trova un debugger di script just-in-time.  
  
 Per implementare un debugger nell'host, è necessario gestire [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). In base a un'azione dell'utente, l'host può alleghiare il debugger e restituire o restituire l'avvio del debugger nel parametro di `pfEnterDebugger` OnScriptErrorDebug. È inoltre necessario implementare questa interfaccia per ottenere la notifica relativa all'errore di run-time anche se non sono presenti debugger esterni che possono essere interpretati dalla gestione del debug dei processi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pErrorDebug`  
 in Errore di run-time che si è verificato.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 out Indica se chiamare [IActiveScriptSiteDebug:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) se l'utente decide di continuare senza eseguire il debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 È inoltre necessario implementare questa interfaccia per ricevere una notifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)