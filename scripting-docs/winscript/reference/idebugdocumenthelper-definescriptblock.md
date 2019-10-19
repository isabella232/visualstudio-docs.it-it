---
title: IDebugDocumentHelper::D efineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576985"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica all'helper che un intervallo di caratteri specifico è un blocco di script gestito dal motore di script specificato.  
  
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
 in Posizione dell'inizio del blocco di script.  
  
 `cChars`  
 in Numero di caratteri nel blocco di script.  
  
 `pas`  
 in Motore di script per questo blocco di script.  
  
 `fScriptlet`  
 in Flag che indica se il blocco di script è un scriptlet.  
  
 `pdwSourceContext`  
 out Contesto di origine per il blocco di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Uno smart host può utilizzare questo metodo quando i documenti contengono blocchi di script incorporati. Un motore di linguaggio può utilizzare questo metodo quando il codice contiene script incorporati per altri linguaggi.  
  
 Il modulo di gestione di script è responsabile di tutta la colorazione della sintassi e delle ricerche del contesto del codice nel blocco di script.  
  
 Il metodo di `DefineScriptBlock` deve essere chiamato dopo l'aggiunta del testo (ad esempio, usando il metodo `IDebugDocumentHelper::AddDBCSText`) ma prima che il blocco di script sia stato analizzato (ad esempio, usando il metodo `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)    
 @No__t_1 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)  
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)