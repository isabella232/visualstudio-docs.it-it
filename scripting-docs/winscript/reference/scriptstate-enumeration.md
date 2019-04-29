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
ms.openlocfilehash: fe6a05c5e73d26a8daa9e46c317422d85d1c40be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840161"
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