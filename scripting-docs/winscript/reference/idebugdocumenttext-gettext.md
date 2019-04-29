---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63e1fee3531272f18c85c23ea83b8ca12920bd2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970861"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera i caratteri e/o gli attributi di carattere associati a un intervallo di posizione del carattere.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cCharacterPosition`  
 [in] Posizione iniziale dell'intervallo di caratteri della posizione.  
  
 `pcharText`  
 [in, out] Un buffer di testo di carattere. Il buffer deve essere sufficientemente grande da contenere `cMaxChars` caratteri. Se questo parametro è NULL, il metodo non restituisce caratteri.  
  
 `pstaTextAttr`  
 [in, out] Un buffer di attributi del carattere. Il buffer deve essere sufficientemente grande da contenere `cMaxChars` caratteri. Se questo parametro è NULL, il metodo non restituisce gli attributi.  
  
 `pcNumChars`  
 [in, out] Il numero di caratteri/attributi restituiti. Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 [in] Numero di caratteri nell'intervallo di posizione di carattere. Specifica inoltre il numero massimo di caratteri da restituire.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera i caratteri e/o gli attributi di carattere associati a un intervallo di posizione del carattere. L'intervallo di posizione del carattere è specificato da una posizione di carattere e un numero di caratteri.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)