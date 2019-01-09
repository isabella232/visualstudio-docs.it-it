---
title: IActiveScriptAuthor::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c434ea17d41fb98300289c3161349f9d9f5a2f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094861"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Aggiunge il nome di un elemento di primo livello dello script dello spazio dei nomi del motore di creazione. Oggetto *elemento di livello radice* è un oggetto che può contenere proprietà e metodi e che può contenere anche un'origine evento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszName`  
 [in] Il nome dell'elemento visualizzato dallo script. Il nome deve essere univoca e persistente.  
  
 `dwFlags`  
 [in] I flag associati con l'elemento denominato. Può essere una combinazione dei valori seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script. Ciò consente l'accesso a proprietà, metodi ed eventi dell'elemento.<br /><br /> Per convenzione, le proprietà dell'elemento includono i membri figlio dell'elemento. Pertanto, tutte le proprietà dell'oggetto figlio e i metodi (e i relativi membri figlio, in modo ricorsivo) sono accessibili.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica gli eventi dell'origine dell'elemento che lo script può avere i gestori di eventi di script.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica che l'elemento è una raccolta di proprietà globali e i metodi che sono associati con lo script. Come i metodi e variabili globali vengono creati i relativi membri.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica che l'elemento deve essere salvato se viene salvato lo script del motore di creazione.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica che l'elemento denominato rappresenta un oggetto di solo codice, e che non è un membro da creare.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica che l'elemento denominato è solo un nome da aggiungere non ha nulla da creare.|  
  
 `pdisp`  
 [in] Il `IDispatch` del `NamedItem` oggetto che viene usato per raccogliere i metodi, proprietà o l'origine dell'evento.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)