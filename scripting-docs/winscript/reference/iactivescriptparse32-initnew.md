---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
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
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561651"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32:: InitNew
Inizializza il motore di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## <a name="remarks"></a>Note  
 Prima di poter usare il motore di scripting, è necessario chiamare uno dei metodi seguenti: `IPersist*::Load`, `IPersist*::InitNew` o `IActiveScriptParse32::InitNew`. La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di script di inizializzarsi automaticamente. Si noti che non è possibile chiamare sia `IPersist*::InitNew` sia `IActiveScriptParse32::InitNew` e `IPersist*::Load`, né è possibile chiamare `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` o `IPersist*::Load` più di una volta.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)