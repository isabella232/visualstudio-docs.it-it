---
title: 'IActiveScriptParse:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573503"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inizializza il motore di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## <a name="remarks"></a>Note  
 Prima di poter usare il motore di scripting, è necessario chiamare uno dei metodi seguenti: `IPersist*::Load`, `IPersist*::InitNew` o `IActiveScriptParse::InitNew`. La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di script di inizializzarsi automaticamente. Si noti che non è possibile chiamare sia `IPersist*::InitNew` sia `IActiveScriptParse::InitNew` e `IPersist*::Load`, né è possibile chiamare `IPersist*::InitNew`, `IActiveScriptParse::InitNew` o `IPersist*::Load` più di una volta.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)