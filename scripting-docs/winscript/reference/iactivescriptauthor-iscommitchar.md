---
title: IActiveScriptAuthor::IsCommitChar | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.IsCommitChar
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::IsCommitChar
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a0b630f872e49b7fbbabf4f354755f900fb4b5e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152129"
---
# <a name="iactivescriptauthoriscommitchar"></a>IActiveScriptAuthor::IsCommitChar
Restituisce un valore che indica se un carattere specificato deve attivare un commit di completamento istruzione dall'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ch`  
 [in] Carattere da testare.  
  
 `pfcommit`  
 [out] `True` se il carattere è un commit carattere; in caso contrario, `False`.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)