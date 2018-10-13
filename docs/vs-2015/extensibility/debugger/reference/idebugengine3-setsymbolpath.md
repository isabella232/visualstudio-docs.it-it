---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63ecd78913f67ff06f0280e4835bb199c4571b70
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240773"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Imposta il percorso o percorsi in cui vengono ricercati i simboli di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Stringa contenente il percorso di ricerca di simboli o i percorsi. Per informazioni dettagliate, vedere "la sezione Osservazioni". Non può essere null.|  
|`szSymbolCachePath`|[in] Stringa contenente il percorso locale in cui possono essere memorizzati nella cache dei simboli. Non può essere null.|  
|`Flags`|[in] Non usato; sempre impostato su 0.|  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 La stringa `szSymbolSearchPath` è un elenco di uno o più percorsi, separati da punti e virgola, per la ricerca dei simboli. Questi percorsi possono essere un percorso locale, un percorso UNC in stile o un URL. Questi percorsi possono essere anche una combinazione di tipi diversi. Se il percorso UNC (ad esempio, \\\Symserver\Symbols), quindi il motore di debug deve determinare se il percorso è in un server di simboli e deve essere in grado di caricare i simboli dai server, memorizzarli nella cache nel percorso specificato da `szSymbolCachePath`.  
  
 Il percorso dei simboli può anche contenere uno o più percorsi di cache. Le cache sono elencate in ordine di priorità, con la cache con priorità più alta prima di tutto e separate da * simboli. Ad esempio:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 Il [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) metodo esegue il carico effettivo dei simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

