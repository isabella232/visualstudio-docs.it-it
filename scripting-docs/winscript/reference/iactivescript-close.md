---
title: IActiveScript::Close | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 886ab1c4c39cf7c64571862bfd28f2fbd1062694
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348803"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Fa sì che il motore di scripting abbandonare tutti gli script attualmente caricato, perdono il proprio stato e rilasciare eventuali puntatori a interfaccia che dispone ad altri oggetti, quindi immettere uno stato chiuso. Sink di evento, il testo script eseguito immediatamente e le chiamate alle macro che sono già in corso vengono completati prima i cambiamenti di stato (usare [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) per annullare un thread in esecuzione di script). Questo metodo deve essere chiamato dall'host di creazione prima del rilascio dell'interfaccia per evitare problemi relativi ai riferimenti circolari.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script era già in stato di chiusura).|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato correttamente, ma lo stato non è stato modificato ancora. Quando i cambiamenti di stato, il sito viene richiamata nel [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) (metodo).|  
|`S_FALSE`|Il metodo ha avuto esito positivo, ma lo script è già stato chiuso.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)