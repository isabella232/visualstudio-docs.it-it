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
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150999"
---
# <a name="iactivescript"></a>IActiveScript
Fornisce i metodi necessari per inizializzare il motore di scripting. Il motore di scripting deve implementare il `IActiveScript` interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Segnala al motore di scripting di [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sito fornito dall'host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera l'oggetto sito associata al motore di Script di Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Inserisce il motore di scripting nello stato specificato.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera lo stato corrente del motore di script.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Fa sì che il motore di scripting abbandonare tutti gli script attualmente caricato, perdono il proprio stato e rilasciare eventuali puntatori a interfaccia che dispone ad altri oggetti, quindi immettere uno stato chiuso.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Aggiunge il nome di un elemento di livello principale a spazio dei nomi del motore di script.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Aggiunge una libreria dei tipi dello spazio dei nomi per lo script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera il `IDispatch` interfaccia per l'esecuzione dello script.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificatore scripting-engine-definite per il thread attualmente in esecuzione.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificatore scripting-engine-definite per il thread associato al thread Win32 Microsoft specificato.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera lo stato corrente di un thread dello script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompe l'esecuzione di un thread in esecuzione di script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Clona il motore di script corrente (meno qualsiasi stato corrente dell'esecuzione), restituendo un motore di script caricato che non dispone di alcun sito nel thread corrente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)