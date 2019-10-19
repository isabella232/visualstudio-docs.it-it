---
title: 'IVariantChangeType:: ChangeType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571776"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Accetta un valore Variant e crea una nuova variante con un tipo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvarDst`  
 [in, out] Variant che contiene il valore rappresentato da `pvarSrc`, ma con il tipo specificato da `vtNew`.  
  
 `pvarSrc`  
 in Valore Variant da modificare in un nuovo tipo.  
  
 `lcid`  
 in Contesto delle impostazioni locali da utilizzare per la conversione degli argomenti in o da stringhe.  
  
 `vtNew`  
 in Specifica il tipo per `pvarDst`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Gli argomenti `pvarDst` e `pvarSrc` possono essere uguali, nel qual caso il valore originale viene sovrascritto. Questo metodo passa `pvarDst` alla funzione `VariantClear` e quindi `pvarDst` deve essere inizializzato su un valore valido.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)