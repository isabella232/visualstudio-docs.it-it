---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf7c39213ae2eb233509d720b7e7c2eab0a17560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839788"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il rango (numero di dimensioni) di una matrice multidimensionale FORTRAN.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce il numero di dimensioni in una matrice multidimensionale FORTRAN.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Commenti  
 Rank indica il numero di dimensioni in una matrice in cui la matrice viene dichiarata come `myarray[1,2,3]` . Questo esempio ha un rango di 3 e 3 dimensioni. Rank non si applica a C++ che usa il concetto di matrice di matrici per ogni dimensione (ovvero `myarray[1][2][3]` ).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
