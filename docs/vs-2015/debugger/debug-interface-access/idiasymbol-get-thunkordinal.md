---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 540eb49b215d06127a47df1defc436a0a307aa6d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64784299"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il tipo di thunk di una funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un valore compreso il [enumerazione THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) enumerazione che specifica il tipo di thunk di una funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Questa proprietà è valida solo se il simbolo come un [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) pari a `SymTagThunk`.  
  
 Un "thunk" è un frammento di codice che esegue la conversione tra uno spazio di indirizzi di memoria a 32 bit (noto anche come spazio di indirizzi flat) e uno spazio di indirizzi di 16 bit (noto come uno spazio degli indirizzi segmentati).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
