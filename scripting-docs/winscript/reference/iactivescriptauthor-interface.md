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
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576162"
---
# <a name="iactivescriptauthor-interface"></a>Interfaccia IActiveScriptAuthor
Rappresenta i servizi di creazione, incluse IntelliSense e le regole di confronto delle informazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IActiveScriptAuthor` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Aggiunge il nome di un elemento di livello radice allo spazio dei nomi del motore di creazione dello script. Un *elemento a livello di radice* è un oggetto che può contenere proprietà e metodi e che può contenere anche un'origine evento.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Aggiunge un scriptlet di codice come figlio dell'oggetto `IScriptNode` a livello radice. Nell'host, il nome completo di scriptlet può avere solo due livelli.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Aggiunge una libreria dei tipi allo spazio dei nomi per lo script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Restituisce il set di caratteri di completamento per un contesto di completamento richiesto.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Restituisce l'oggetto scriptlet con gli attributi specificati.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Restituisce le informazioni sul tipo e le posizioni di ancoraggio per un determinato carattere in un blocco di codice. Vengono fornite informazioni per IntelliSense membro, elenchi globali e suggerimenti per i parametri.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Restituisce informazioni sulla lingua.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Restituisce la radice `IScriptNode` della struttura ad albero di script dell'autore.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Restituisce gli attributi di testo di un scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Restituisce gli attributi di testo di un blocco di script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Restituisce un valore che indica se un carattere specificato deve eseguire il commit di un completamento di istruzione da parte dell'applicazione.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizza il testo dello script, aggiunge il testo al motore di creazione degli script di creazione e crea un `IScriptEntry` oggetto che corrisponde al blocco di script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Rimuove un oggetto `NamedItem` dallo spazio dei nomi del motore di creazione degli script.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Rimuove una libreria dei tipi dallo spazio dei nomi del motore di creazione degli script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)