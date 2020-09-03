---
title: IDiaSymbol::get_isMatrixRowMajor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff6b8523d9f4e3cbf01727c6d98804f71b518912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163984"
---
# <a name="idiasymbolget_ismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica se la matrice è la riga principale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT get_isMatrixRowMajor(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Puntatore a un oggetto `BOOL` che specifica se la matrice è la riga principale.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
