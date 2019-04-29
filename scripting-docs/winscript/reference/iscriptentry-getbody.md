---
title: IScriptEntry::GetBody | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f8f1ad24660401d575af2724b788387fd546af8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787879"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Restituisce il testo che corrisponde al corpo di un `IScriptEntry` blocco di script, blocco della funzione o scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstr`  
 [out] Il testo presente nel corpo di una delle operazioni seguenti:  
  
- Un `IScriptEntry` blocco di script  
  
- Un `IScriptEntry` funzione in un blocco (funzione)  
  
- Un `IScriptEntry` scriptlet gestore dell'evento  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)