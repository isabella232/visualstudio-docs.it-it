---
title: Enumerazione SCRIPTGCTYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b25ffb530bf16fff0008bb73b55ecb0c523efe0d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349101"
---
# <a name="scriptgctype-enumeration"></a>Enumerazione SCRIPTGCTYPE
Il tipo di garbage collection da eseguire. Utilizzato nel [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|È normale procedura di garbage collection. Il valore integer è 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Tale operazione completa di garbage collection. Il valore intero è 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)