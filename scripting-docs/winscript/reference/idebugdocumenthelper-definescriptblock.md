---
title: 'Idebugdocumenthelper:: Definescriptblock | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0037df270bc95faaba4d2f04cce65902d08dc6e9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087997"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica all'helper che un determinato intervallo di caratteri è un blocco di script che viene gestito dal motore di script specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ulCharOffset`  
 [in] Posizione di inizio del blocco di script.  
  
 `cChars`  
 [in] Numero di caratteri nel blocco di script.  
  
 `pas`  
 [in] Il motore di script di questo blocco di script.  
  
 `fScriptlet`  
 [in] Flag che indica se il blocco di script è scriptlet.  
  
 `pdwSourceContext`  
 [out] Il contesto di origine per il blocco di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host può utilizzare questo metodo quando i documenti contengono blocchi di script incorporati. Un motore del linguaggio può utilizzare questo metodo quando il codice contiene script incorporati per le altre lingue.  
  
 Il motore di script è responsabile di tutte le sintassi colorazione e il codice contesto ricerche nel blocco di script.  
  
 Il `DefineScriptBlock` deve essere chiamato dopo il testo è stato aggiunto (ad esempio, usando il `IDebugDocumentHelper::AddDBCSText` (metodo)) ma prima lo script di blocco è stato analizzato (ad esempio, usando il `IActiveScriptParse ::ParseScriptText` (metodo)).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)