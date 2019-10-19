---
title: 'IActiveScriptAuthor:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577253"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Aggiunge il nome di un elemento di livello radice allo spazio dei nomi del motore di creazione dello script. Un *elemento a livello di radice* è un oggetto che può contenere proprietà e metodi e che può contenere anche un'origine evento.  
  
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
 in Nome dell'elemento visualizzato dallo script. Il nome deve essere univoco e permanente.  
  
 `dwFlags`  
 in Flag associati all'elemento specificato. Può essere una combinazione dei valori seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script. Questo consente l'accesso alle proprietà, ai metodi e agli eventi dell'elemento.<br /><br /> Per convenzione, le proprietà dell'elemento includono i membri figlio dell'elemento. Pertanto, tutti i metodi e le proprietà dell'oggetto figlio (e i relativi membri figlio, in modo ricorsivo) sono accessibili.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica gli eventi dell'origine dell'elemento che lo script può avere gestori di eventi di script.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica che l'elemento è una raccolta di proprietà globali e metodi associati allo script. I membri vengono creati come variabili e metodi globali.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica che l'elemento deve essere salvato nel caso in cui venga salvato il motore di creazione degli script.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica che l'elemento denominato rappresenta un oggetto di solo codice e non dispone di un membro da creare.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica che l'elemento denominato è semplicemente un nome da aggiungere e non ha nulla da creare.|  
  
 `pdisp`  
 in @No__t_0 dell'oggetto `NamedItem` utilizzato per raccogliere metodi, proprietà o l'origine dell'evento.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)