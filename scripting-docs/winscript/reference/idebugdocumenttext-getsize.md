---
title: IDebugDocumentText::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95f8df44a503fa72f57a9cee17eb5e832e4eb670
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153997"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Restituisce il numero di righe e numero di caratteri nel documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcNumLines`  
 [out] Numero di righe nel documento. Se questo parametro è NULL, il metodo non restituisce un valore.  
  
 `pcNumChars`  
 [out] Numero di caratteri nel documento. Se questo parametro è NULL, il metodo non restituisce un valore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il numero di righe e numero di caratteri nel documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)