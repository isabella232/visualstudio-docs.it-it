---
title: 'IActiveScript:: AddNamedItem | Microsoft Docs'
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
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575818"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Aggiunge il nome di un elemento di livello radice allo spazio dei nomi del motore di script. Un elemento a livello di radice è un oggetto con proprietà e metodi, un'origine evento o tutti e tre.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrName`  
 in Indirizzo di un buffer che contiene il nome dell'elemento visualizzato dallo script. Il nome deve essere univoco e permanente.  
  
 `dwFlags`  
 in Flag associati a un elemento. Può essere una combinazione di questi valori:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica che l'elemento denominato rappresenta un oggetto di solo codice e che l'host non dispone di `IUnknown` da associare a questo oggetto di solo codice. L'host ha solo un nome per questo oggetto. Nei linguaggi orientati a oggetti C++, ad esempio, questo flag crea una classe. Non tutti i linguaggi supportano questo flag.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica che l'elemento è una raccolta di proprietà globali e metodi associati allo script. In genere, un motore di script ignora il nome dell'oggetto (ad eccezione di per usarlo come cookie per il metodo [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) o per la risoluzione dell'ambito esplicito) ed espone i membri come variabili e metodi globali. In questo modo l'host può estendere la libreria (funzioni di run-time e così via) disponibile per lo script. Viene lasciata al motore di scripting per gestire i conflitti di nomi, ad esempio quando due elementi SCRIPTITEM_GLOBALMEMBERS hanno metodi con lo stesso nome, sebbene non venga restituito un errore a causa di questa situazione.|  
|SCRIPTITEM_ISPERSISTENT|Indica che l'elemento deve essere salvato se il motore di scripting viene salvato. Analogamente, l'impostazione di questo flag indica che una transizione allo stato inizializzato deve conservare le informazioni sul tipo e sul nome dell'elemento. il motore di scripting, tuttavia, deve rilasciare tutti i puntatori alle interfacce dell'oggetto effettivo.|  
|SCRIPTITEM_ISSOURCE|Indica che l'elemento genera eventi che lo script può affondare. Gli oggetti figlio (proprietà dell'oggetto che sono oggetti stessi) possono inoltre generare eventi nello script. Questo non è ricorsivo, ma fornisce un meccanismo pratico per il caso comune, ad esempio, per la creazione di un contenitore e di tutti i relativi controlli membro.|  
|SCRIPTITEM_ISVISIBLE|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script, consentendo l'accesso alle proprietà, ai metodi e agli eventi dell'elemento. Per convenzione, le proprietà dell'elemento includono gli elementi figlio dell'elemento; Pertanto, tutti i metodi e le proprietà degli oggetti figlio (e i relativi elementi figlio in modo ricorsivo) saranno accessibili.|  
|SCRIPTITEM_NOCODE|Indica che l'elemento è semplicemente un nome aggiunto allo spazio dei nomi dello script e non deve essere considerato come un elemento per cui il codice deve essere associato. Se, ad esempio, non si imposta questo flag, VBScript creerà un modulo separato per l'elemento denominato e C++ potrebbe creare una classe wrapper separata per l'elemento specificato.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)