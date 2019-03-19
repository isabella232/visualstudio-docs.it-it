---
title: IVariantChangeType::ChangeType | Microsoft Docs
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
ms.openlocfilehash: 81ed0a8502e9b0cfc53725621d477d34ee5010ea
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158581"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Accetta un valore variant e crea una nuova variante con il tipo specificato.  
  
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
 [in, out] Una variante che contenga il valore rappresentato da `pvarSrc`, ma con il tipo specificato dal `vtNew`.  
  
 `pvarSrc`  
 [in] Un valore variant per modificare in un nuovo tipo.  
  
 `lcid`  
 [in] Il contesto delle impostazioni locali da usare durante la conversione di argomenti a o da stringhe.  
  
 `vtNew`  
 [in] Specifica il tipo per `pvarDst` diventi.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il `pvarDst` e `pvarSrc` argomenti che può essere uguali, nel qual caso il valore originale viene sovrascritto. Questo metodo passa `pvarDst` per il `VariantClear` funzione e, di conseguenza `pvarDst` deve essere inizializzato su un valore valido.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)