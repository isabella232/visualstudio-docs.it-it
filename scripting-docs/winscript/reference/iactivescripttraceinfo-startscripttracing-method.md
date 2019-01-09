---
title: 'Metodo iactivescripttraceinfo:: Startscripttracing | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6462597f55b6b0ceee885d207572e9669a350600
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093642"
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
  
1.  S_OK: Operazione completata.  
  
2.  E_POINTER: `pSiteTraceInfo` è un puntatore NULL.  
  
3.  E_NOTIMPL: Non implementato.