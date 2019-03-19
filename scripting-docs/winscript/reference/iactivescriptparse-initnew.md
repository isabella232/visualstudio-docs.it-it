---
title: IActiveScriptParse::InitNew | Microsoft Docs
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
ms.openlocfilehash: 55d38031708694aa777f7598f261afdfc2b4f3b9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148948"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inizializza il motore di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## <a name="remarks"></a>Note  
 Prima di poter usare il motore di scripting, è necessario chiamare uno dei seguenti metodi: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse::InitNew`. La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di scripting per l'inizializzazione. Si noti che non è valido per chiamare entrambe `IPersist*::InitNew` oppure `IActiveScriptParse::InitNew` e `IPersist*::Load`, non è valido per chiamare `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, o `IPersist*::Load` più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)