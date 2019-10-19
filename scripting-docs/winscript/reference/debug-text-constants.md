---
title: Costanti DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577374"
---
# <a name="debug_text-constants"></a>Costanti DEBUG_TEXT
Usato durante [IDebugExpressionContext::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION DWORD|0x00000001|Indica che il testo è un'espressione anziché un'istruzione. Questo flag può influire sul modo in cui il testo viene analizzato da alcune lingue.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se è disponibile un valore restituito, esso verrà usato dal chiamante.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Non consentire effetti collaterali. Se questo flag è impostato, la valutazione dell'espressione non deve modificare lo stato di Runtime.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Consentire i punti di interruzione durante la valutazione del testo. Se questo flag non è impostato, i punti di interruzione verranno ignorati durante la valutazione del testo.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Consente le segnalazioni degli errori durante la valutazione del testo. Se questo flag non è impostato, gli errori non verranno segnalati all'host durante la valutazione.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica che l'espressione deve essere valutata in un contesto di codice anziché eseguire l'espressione stessa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)