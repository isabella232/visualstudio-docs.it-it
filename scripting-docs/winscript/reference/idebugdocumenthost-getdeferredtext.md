---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f20b090f880168b3561cba547db319813ba3fe02
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148073"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Restituisce un intervallo di caratteri che sono state aggiunte mediante la `IDebugDocumentHelper::AddDeferredText` metodo, in modo che il documento originale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwTextStartCookie`  
 [in] Cookie definito dall'host che rappresenta la posizione iniziale del testo.  
  
 `pcharText`  
 [in, out] Un buffer di testo di carattere. Questo metodo non restituisce caratteri se questo parametro è `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Un buffer di attributi del carattere. Questo metodo non restituisce attributi se questo parametro è `NULL`.  
  
 `pcNumChars`  
 [in, out] Indica il numero effettivo di caratteri/attributi restituiti. Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 [in] Il numero massimo di caratteri da restituire.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo può restituire `E_NOTIMPL`, se l'host non chiama `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Questo metodo restituisce il testo dal documento originale. L'host non tenere traccia di modifiche o altre modifiche al documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)