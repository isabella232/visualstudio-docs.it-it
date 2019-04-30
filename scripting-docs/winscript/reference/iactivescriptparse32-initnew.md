---
title: IActiveScriptParse32::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 685c596caa61a5cbd5042fad3a1bfb39c349c1b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009424"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inizializza il motore di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## <a name="remarks"></a>Note  
 Prima di poter usare il motore di scripting, è necessario chiamare uno dei seguenti metodi: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse32::InitNew`. La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di scripting per l'inizializzazione. Si noti che non è valido per chiamare entrambe `IPersist*::InitNew` oppure `IActiveScriptParse32::InitNew` e `IPersist*::Load`, non è valido per chiamare `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, o `IPersist*::Load` più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)