---
title: 'IActiveScriptAuthor:: GetLanguageFlags | Microsoft Docs'
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
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576195"
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
 out Flag che contengono informazioni sulla lingua. Può essere una combinazione dei valori seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Il linguaggio preferisce la creazione di gestori eventi di script da parte del motore di creazione script anziché dell'applicazione.|  
|fasaSupportInternalHandler|0x0002|Il linguaggio supporta i gestori eventi di script creati dal motore di creazione degli script.|  
|fasaCaseSensitive|0x0004|Il linguaggio di script distingue tra maiuscole e minuscole.|  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Se il motore di creazione degli script gestisce i gestori eventi, l'applicazione deve chiamare `CreateChildHandler` da un oggetto `IScriptEntry`. Viene creato un oggetto `IScriptScriptlet` che corrisponde al gestore eventi. Il motore aggiunge anche un gestore eventi alla voce di script. Il gestore eventi è una funzione vuota che contiene le informazioni sulla firma specificate.  
  
 Se l'applicazione gestisce i gestori eventi, deve chiamare `CreateChildHandler` da un oggetto `IScriptNode` che rappresenta un gestore eventi scriptlet. Viene creato un oggetto `IScriptScriptlet` associato al gestore eventi scriptlet. L'applicazione deve inoltre aggiungere una funzione vuota come gestore eventi a un oggetto `IScriptEntry` nuovo o esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)