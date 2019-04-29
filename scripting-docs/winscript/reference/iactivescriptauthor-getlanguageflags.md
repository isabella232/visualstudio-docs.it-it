---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9f1a68db05ac0d909108ce77587ae4b071c9a2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935471"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Restituisce informazioni sulla lingua.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pgrfasa`  
 [out] Flag che contengono informazioni sulla lingua. Può essere una combinazione dei valori seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Il linguaggio preferenziale per la creazione del gestore di evento script dallo script di creazione motore invece che all'applicazione.|  
|fasaSupportInternalHandler|0x0002|Il linguaggio supporta i gestori di eventi di script creati dallo script del motore di creazione.|  
|fasaCaseSensitive|0x0004|Il linguaggio di scripting viene fatta distinzione tra maiuscole e minuscole.|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Se lo script del motore di creazione consente di gestire i gestori eventi, l'applicazione deve chiamare `CreateChildHandler` da un `IScriptEntry` oggetto. Verrà creato un `IScriptScriptlet` oggetto corrispondente al gestore dell'evento. Il motore aggiunge anche un gestore eventi per la voce di script. Il gestore dell'evento è una funzione vuota che contiene le informazioni sulla firma specificato.  
  
 Se l'applicazione a gestire i gestori eventi, questo deve chiamare `CreateChildHandler` da un `IScriptNode` oggetto che rappresenta un scriptlet di gestore dell'evento. Verrà creato un `IScriptScriptlet` oggetto che è associato lo scriptlet di gestore dell'evento. L'applicazione dispone anche di aggiungere una funzione vuota come un evento gestore a un nuovo o esistente `IScriptEntry` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)