---
title: 'Metodo iactivescripttraceinfo:: Startscripttracing | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b87971e1fd2e484aa54ff4de56ee56e00b19b1e6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101015"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>Metodo IActiveScriptTraceInfo::StartScriptTracing
Avvia traccia degli script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parametri  
 `pSiteTraceInfo`  
 Puntatore a IActiveScriptSiteTraceInfo dell'host.  
  
 `guidContextId`  
 Il GUID del contesto.  
  
## <a name="return-value"></a>Valore restituito  
 I valori restituiti possibili per questo metodo sono quanto segue:  
  
1. S_OK: Operazione completata.  
  
2. E_POINTER: `pSiteTraceInfo` è un puntatore NULL.  
  
3. E_NOTIMPL: Non implementato.