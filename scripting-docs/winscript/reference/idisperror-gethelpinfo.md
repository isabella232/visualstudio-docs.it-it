---
title: 'IDispError:: GetHelpInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573128"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Restituisce il percorso del file della guida e l'ID del contesto dell'argomento che spiega l'errore, se possibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrFileName`  
 out Stringa contenente il percorso completo del file della guida. Se non è presente alcun file della guida o si verifica un errore, il valore restituito è NULL.  
  
 `pdwContext`  
 out ID del contesto della Guida per l'errore. Se non è presente alcun file della guida (se `pbstrFileName` è NULL), questo parametro non ha alcun significato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Si è verificato un errore specifico del provider.|  
|`E_INVALIDARG`|`pbstrFileName` o `pdwContext` è NULL.|  
|`E_OUTOFMEMORY`|Il provider non è in grado di allocare memoria sufficiente per restituire il percorso del file della guida.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il percorso del file della guida e l'ID del contesto dell'argomento che spiega l'errore, se possibile.  
  
> [!NOTE]
> Questo metodo non è implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)