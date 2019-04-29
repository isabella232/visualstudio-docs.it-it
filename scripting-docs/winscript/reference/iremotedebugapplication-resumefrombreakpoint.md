---
title: IRemoteDebugApplication::ResumeFromBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5844381188cb03c99ab0a44ed9b9e0fdbab67e6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944166"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continua un'applicazione che è attualmente disponibile in un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prptFocus`  
 [in] Per l'esecuzione di istruzioni modalità, il thread che deve essere interessata dalla modalità di debug passo a passo.  
  
 `bra`  
 [in] L'azione da eseguire dopo il ripristino dell'applicazione.  
  
 `era`  
 [in] L'azione da intraprendere nel caso in cui l'applicazione è stata arrestata a causa di un errore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo continua a un'applicazione che è attualmente disponibile in un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)