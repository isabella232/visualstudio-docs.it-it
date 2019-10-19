---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577241"
---
# <a name="iactivescript"></a>IActiveScript
Fornisce i metodi necessari per inizializzare il motore di scripting. Il motore di scripting deve implementare l'interfaccia `IActiveScript`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informa il motore di scripting del sito [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fornito dall'host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera l'oggetto sito associato al motore di Windows script.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Inserisce il motore di scripting nello stato specificato.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera lo stato corrente del motore di script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Fa in modo che il motore di script abbandoni tutti gli script attualmente caricati, perda il proprio stato e rilasci tutti i puntatori di interfaccia che contiene ad altri oggetti, entrando quindi in uno stato chiuso.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Aggiunge il nome di un elemento di livello radice allo spazio dei nomi del motore di script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Aggiunge una libreria dei tipi allo spazio dei nomi per lo script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera l'interfaccia `IDispatch` per lo script in esecuzione.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificatore definito dal motore di script per il thread attualmente in esecuzione.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificatore definito dal motore di script per il thread associato al thread Microsoft Win32 specificato.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera lo stato corrente di un thread di script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompe l'esecuzione di un thread di script in esecuzione.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona il motore di scripting corrente (meno qualsiasi stato di esecuzione corrente), restituendo un motore di script caricato senza sito nel thread corrente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)