---
title: Interfaccia IActiveScriptAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b3d9725d72f5213aadc3d9400bef87cecb20ba0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159296"
---
# <a name="iactivescriptauthor-interface"></a>Interfaccia IActiveScriptAuthor
Rappresenta la creazione di servizi, tra cui IntelliSense e le regole di confronto delle informazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IActiveScriptAuthor` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Aggiunge il nome di un elemento di primo livello dello script dello spazio dei nomi del motore di creazione. Oggetto *elemento di livello radice* è un oggetto che può contenere proprietà e metodi e che può contenere anche un'origine evento.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Aggiunge un scriptlet di codice come figlio del livello radice `IScriptNode` oggetto. Sull'host, il nome completo dello scriptlet può avere solo due livelli.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Aggiunge una libreria dei tipi dello spazio dei nomi per lo script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Restituisce il set di caratteri di completamento per un contesto di richiesta di completamento.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Restituisce lo scriptlet che ha gli attributi specificati.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Restituisce digitare le informazioni e le posizioni di ancoraggio per un determinato carattere in un blocco di codice. Fornisce informazioni per il membro IntelliSense, gli elenchi globali e suggerimenti relativi ai parametri.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Restituisce informazioni sulla lingua.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Restituisce il `IScriptNode` radice dell'albero di script dell'autore.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Restituisce gli attributi di testo di scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Restituisce gli attributi di testo di un blocco di script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Restituisce un valore che indica se un carattere specificato deve eseguire il commit di un completamento delle istruzioni dall'applicazione.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizza il testo dello script, aggiunge il testo dello script di creazione e modifica del motore di creazione e crea un `IScriptEntry` oggetto che corrisponde al blocco di script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Rimuove un `NamedItem` oggetto dallo spazio dei nomi dello script del motore di creazione.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Rimuove lo script dello spazio dei nomi del motore di creazione di una libreria dei tipi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)