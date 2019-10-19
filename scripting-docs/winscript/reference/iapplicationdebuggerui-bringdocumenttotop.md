---
title: 'IApplicationDebuggerUI:: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577801"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Consente di portare la finestra contenente il documento di debug specificato nella parte superiore dell'interfaccia utente del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pddt`  
 in Eseguire il debug del documento per portarlo nella parte superiore dell'interfaccia utente del debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Il documento non è noto.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente di portare la finestra contenente il documento di debug specificato nella parte superiore dell'interfaccia utente del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)