---
title: IDebugApplication::StepOutComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04f8ecfb835199afa0a60f3fde3c8fbdc8812240
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153136"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Notifica il gestore di debug di processi che un motore di lingua nella modalità passo a passo sta per essere restituita al relativo chiamante.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Motori di linguaggio chiamano questo metodo in modalità solo passaggio prima di restituire al chiamante. Il gestore di debug di processi Usa questa opportunità per notificare a tutti gli altri motori di script che interrompano il prima possibile. Questa tecnica è il passaggio tra più linguaggi come vengono implementate le modalità.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)