---
title: 'IDebugDocumentText:: GetText | Microsoft Docs'
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
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572078"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera i caratteri e/o gli attributi carattere associati a un intervallo di posizioni dei caratteri.  
  
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
 in Posizione iniziale dell'intervallo di posizioni dei caratteri.  
  
 `pcharText`  
 [in, out] Buffer di testo di tipo carattere. Il buffer deve essere sufficientemente grande da contenere `cMaxChars` caratteri. Se questo parametro è NULL, il metodo non restituisce caratteri.  
  
 `pstaTextAttr`  
 [in, out] Buffer dell'attributo character. Il buffer deve essere sufficientemente grande da contenere `cMaxChars` caratteri. Se questo parametro è NULL, il metodo non restituisce gli attributi.  
  
 `pcNumChars`  
 [in, out] Numero di caratteri/attributi restituiti. Questo parametro deve essere impostato su zero prima di chiamare questo metodo.  
  
 `cMaxChars`  
 in Numero di caratteri nell'intervallo di posizioni dei caratteri. Specifica anche il numero massimo di caratteri da restituire.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo recupera i caratteri e/o gli attributi carattere associati a un intervallo di posizioni dei caratteri. L'intervallo di posizioni dei caratteri viene specificato da una posizione del carattere e da un numero di caratteri.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)    
 [Enumerazione SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)