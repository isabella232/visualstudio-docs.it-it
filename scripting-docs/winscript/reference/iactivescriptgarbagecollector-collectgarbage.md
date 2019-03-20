---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144667"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
L'host di Script ActiveX chiama questo metodo per avviare l'operazione di garbage collection.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametri  
 `scriptgctype`  
 [in] Il [enumerazione SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) che specifica se eseguire completo o normale procedura di garbage collection.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un HRESULT.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptGarbageCollector](../../winscript/reference/iactivescriptgarbagecollector-interface.md)