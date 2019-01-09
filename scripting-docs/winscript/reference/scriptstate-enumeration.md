---
title: Enumerazione SCRIPTSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff935e54e42eef6691948a7e0d91a495c5153adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097799"
---
# <a name="scriptstate-enumeration"></a>Enumerazione SCRIPTSTATE
Specifica lo stato di un motore di scripting. Questa enumerazione viene utilizzata per la [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) , e [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metodi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|Lo script è stato appena creato, ma non è ancora stato inizializzato con un `IPersist*` interfaccia e [IActiveScript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Script è stato inizializzato, ma non è in esecuzione (la connessione ad altri oggetti o eventi di sink) o l'esecuzione di qualsiasi codice. È possibile eseguire query codice per l'esecuzione chiamando il [iactivescriptparse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) (metodo).|  
|SCRIPTSTATE_STARTED|Lo script può eseguire il codice, ma non è ancora sink gli eventi di oggetti aggiunti per il [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) (metodo).|  
|SCRIPTSTATE_CONNECTED|Lo script è caricato e connesso agli eventi di sink.|  
|SCRIPTSTATE_DISCONNECTED|Lo script viene caricato e ha uno stato di esecuzione, ma è temporaneamente disconnesso dagli eventi di sink.|  
|SCRIPTSTATE_CLOSED|Lo script è stato chiuso. Il motore di scripting non funziona più e restituisce gli errori per la maggior parte dei metodi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)