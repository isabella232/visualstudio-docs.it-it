---
title: 'IActiveScriptSiteInterruptPoll:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572231"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Consente a un host di specificare che uno script deve terminare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|La chiamata ha avuto esito positivo e l'host consente di continuare l'esecuzione dello script.|  
|`S_FALSE`|La chiamata ha avuto esito positivo e l'host richiede che lo script venga terminato.|  
  
## <a name="remarks"></a>Note  
 Lo script Hosted deve terminare a meno che non venga `S_OK` il valore restituito del metodo `QueryContinue`. Un valore restituito di `S_FALSE` indica che l'host richiede in modo esplicito che lo script venga terminato.  
  
 Un host multithread può utilizzare il metodo `IActiveScript::InterruptScriptThread` per terminare uno script.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)    
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)