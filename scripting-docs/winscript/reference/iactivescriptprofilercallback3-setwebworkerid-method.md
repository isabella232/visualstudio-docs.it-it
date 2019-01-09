---
title: Metodo IActiveScriptProfilerCallback3::SetWebWorkerId | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094433"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Metodo IActiveScriptProfilerCallback3::SetWebWorkerId
Notifica al profiler sull'ID del ruolo di lavoro da usare per questa sessione di profilatura. Se la funzione non è in esecuzione nel contesto della pagina, questo metodo non viene richiamato. Il valore di `webWorkerId` viene incrementata di 1 per ogni thread di lavoro, a partire da 1. I valori di ID non sono progettati per essere stabile oltre una sessione e corrispondono solo per l'ordine in cui sono stati creati i ruoli di lavoro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `webWorkerId`  
 L'ID del ruolo di lavoro web.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di script.