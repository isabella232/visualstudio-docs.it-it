---
title: 'Metodo metodo ijsdebugdatatarget:: ReadNullTerminatedString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572407"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Metodo IJsDebugDataTarget::ReadNullTerminatedString
Legge il numero specificato di caratteri dalla destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `address`  
 in Indirizzo da cui leggere.  
  
 `characterSize`  
 [in] dimensione di ogni carattere nella stringa  
  
 `maxCharacters`  
 in Numero massimo di caratteri da leggere. maxCharacters deve essere ragionevole. Eventuali richieste di oltre 128 MB di memoria avranno esito negativo.  Se la stringa è maggiore di maxCharacters, la stringa di risultato verrà troncata dopo maxCharacters.  
  
 `pString`  
 out BSTR letto dalla destinazione.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce S_FALSE se troncato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)