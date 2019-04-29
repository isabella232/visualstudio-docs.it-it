---
title: ISetNextStatement::CanSetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb65faaf107c42b44201ea18c1150f8093b1654c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786615"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Questo metodo determina se il punto di esecuzione, che determina la successiva istruzione di codice da eseguire, è possibile impostare nel percorso specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStackFrame`  
 [in] Puntatore a un oggetto stack frame.  
  
 `pCodeContext`  
 [in] Puntatore a un oggetto di contesto del codice.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|L'istruzione successiva può essere aggiornato nel contesto del codice specificato.|  
|`S_FALSE`|L'istruzione successiva non è possibile aggiornare il contesto del codice specificato.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)