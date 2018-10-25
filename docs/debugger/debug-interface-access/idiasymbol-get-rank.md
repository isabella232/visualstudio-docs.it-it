---
title: Get_rank | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc12e9251bd452edc3fdede1a5f7414462162301
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847695"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Recupera la classificazione (numero di dimensioni) di una matrice multidimensionale di FORTRAN.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di dimensioni in una matrice multidimensionale di FORTRAN.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Numero di dimensioni si riferisce al numero di dimensioni nella matrice in cui la matrice viene dichiarata come `myarray[1,2,3]`. Questo esempio è presente un rango pari a 3 e 3 dimensioni. Numero di dimensioni non si applica a C++ che usa il concetto di una matrice di matrici per ogni dimensione (vale a dire `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)