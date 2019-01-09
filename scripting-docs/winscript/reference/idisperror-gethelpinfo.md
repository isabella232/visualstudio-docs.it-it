---
title: IDispError::GetHelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8c2c8ae3a3cff2485c50901bb94ced83098e6000
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087490"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Restituisce il percorso del file della Guida e l'ID del contesto dell'argomento che spiega l'errore, se possibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrFileName`  
 [out] Stringa contenente il percorso completo del file della Guida. Se è presente alcun file della Guida in linea oppure si verifica un errore, il valore restituito è NULL.  
  
 `pdwContext`  
 [out] L'ID del contesto della Guida per l'errore. Se è presente alcun file della Guida (se `pbstrFileName` è NULL), questo parametro non ha alcun significato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Si è verificato un errore specifico del provider.|  
|`E_INVALIDARG`|`pbstrFileName` o `pdwContext` era NULL.|  
|`E_OUTOFMEMORY`|Il provider non è riuscito ad allocare memoria sufficiente nella quale restituire il percorso del file della Guida.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il percorso del file della Guida e l'ID del contesto dell'argomento che spiega l'errore, se possibile.  
  
> [!NOTE]
>  Questo metodo non è implementato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)