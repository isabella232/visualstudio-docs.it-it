---
title: IActiveScript::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db0a97c01d948a0c26850ebd1c3f47c6e3900614
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935797"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Aggiunge il nome di un elemento di livello radice per lo spazio dei nomi del motore di script. Un elemento di livello radice è un oggetto con proprietà e metodi, un'origine evento o tutti e tre.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrName`  
 [in] Indirizzo di un buffer che contiene il nome dell'elemento visualizzato dallo script. Il nome deve essere univoca e persistente.  
  
 `dwFlags`  
 [in] Flag associato a un elemento. Può essere una combinazione dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica che l'elemento denominato rappresenta un oggetto di solo codice, e che l'host non ha `IUnknown` da associare a questo oggetto di solo codice. L'host ha solo un nome per questo oggetto. Nei linguaggi orientate a oggetti, ad esempio C++, questo flag creerà una classe. Non tutti i linguaggi supportano questo flag.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica che l'elemento è una raccolta di proprietà globali e i metodi associati allo script. In genere, un motore di script ignora il nome dell'oggetto (diverso da quello allo scopo di utilizzarlo come un cookie per la [iactivescriptsite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metodo, o per la risoluzione dell'ambito esplicito) ed esporre i relativi membri come globale le variabili e metodi. In questo modo l'host estendere la libreria (funzioni di runtime e così via) disponibile per lo script. Si è lasciato al motore di script per gestire con il nome è in conflitto (ad esempio, quando due elementi SCRIPTITEM_GLOBALMEMBERS dispongono di metodi con lo stesso nome), anche se non deve essere restituito un errore a causa di questa situazione.|  
|SCRIPTITEM_ISPERSISTENT|Indica che l'elemento deve essere salvato se il motore di scripting viene salvato. Analogamente, l'impostazione di questo flag indica che una transizione allo stato inizializzato deve mantenere le informazioni di nome e il tipo dell'elemento (il motore di scripting deve, tuttavia, rilasciare tutti i puntatori alle interfacce per l'oggetto effettivo).|  
|SCRIPTITEM_ISSOURCE|Indica che l'elemento genera eventi che possa includere lo script. Gli oggetti figlio (proprietà dell'oggetto che sono di per sé oggetti) possono anche l'origine degli eventi per lo script. Questo non è ricorsivo, ma fornisce un comodo meccanismo per il caso comune, ad esempio, di creazione di un contenitore e tutti i relativi membri controlli.|  
|SCRIPTITEM_ISVISIBLE|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script, che consente l'accesso per la proprietà, metodi ed eventi dell'elemento. Per convenzione le proprietà dell'elemento includono elementi figlio dell'elemento; Pertanto, tutte le proprietà dell'oggetto figlio e i metodi (e i relativi elementi figlio, in modo ricorsivo) saranno accessibili.|  
|SCRIPTITEM_NOCODE|Indica che l'elemento è semplicemente un nome da aggiungere allo spazio dei nomi dello script e non deve essere considerato un elemento per il quale codice deve essere associato. Ad esempio, se questo flag non impostato, VBScript verrà creato un modulo separato per l'elemento denominato e C++ potrebbe creare una classe wrapper separato per l'elemento denominato.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)