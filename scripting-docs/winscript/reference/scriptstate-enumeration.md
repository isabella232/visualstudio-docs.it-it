---
title: Enumerazione SCRIPTSTATE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575675"
---
# <a name="scriptstate-enumeration"></a>Enumerazione SCRIPTSTATE
Specifica lo stato di un motore di script. Questa enumerazione viene utilizzata dai metodi [IActiveScript:: GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) e [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
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
|SCRIPTSTATE_UNINITIALIZED|Lo script è stato appena creato, ma non è ancora stato inizializzato usando un'interfaccia `IPersist*` e [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|Lo script è stato inizializzato, ma non è in esecuzione (connessione ad altri oggetti o eventi di sink) o in esecuzione di qualsiasi codice. È possibile eseguire query sul codice per l'esecuzione chiamando il metodo [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|Lo script può eseguire codice, ma non sta ancora affondando gli eventi degli oggetti aggiunti dal metodo [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|Lo script viene caricato e connesso per gli eventi di sink.|  
|SCRIPTSTATE_DISCONNECTED|Lo script viene caricato e ha uno stato di esecuzione in fase di esecuzione, ma è temporaneamente disconnesso dagli eventi sink.|  
|SCRIPTSTATE_CLOSED|Lo script è stato chiuso. Il motore di scripting non funziona più e restituisce gli errori per la maggior parte dei metodi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)