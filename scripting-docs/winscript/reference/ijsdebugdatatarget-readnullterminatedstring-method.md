---
title: 'Metodo ijsdebugdatatarget:: Readnullterminatedstring | Microsoft Docs'
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
ms.openlocfilehash: 178a2d3705e4904de9253c02319f6ba94e567d76
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146656"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Metodo IJsDebugDataTarget::ReadNullTerminatedString
Legge il numero di caratteri specificato dalla destinazione.  
  
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
 [in] L'indirizzo da cui leggere.  
  
 `characterSize`  
 [in] dimensione di ogni carattere nella stringa  
  
 `maxCharacters`  
 [in] Il numero massimo di caratteri da leggere. valore di maxCharacters deve essere accettabile. Qualsiasi richiesta per più di 128MB di memoria avrà esito negativo.  Se la stringa è maggiore di maxCharacters, la stringa di risultato verrà troncata dopo il valore di maxCharacters.  
  
 `pString`  
 [out] La stringa BSTR letta dalla destinazione.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce S_FALSE se troncato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)