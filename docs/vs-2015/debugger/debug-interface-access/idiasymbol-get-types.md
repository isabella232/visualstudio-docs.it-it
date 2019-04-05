---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e67ce18d261843fecb04f92a09bd48c271e5105
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954402"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una matrice di tipi specifici del compilatore per questo simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cTypes`  
 [in] Dimensione del buffer per contenere i dati.  
  
 `pcTypes`  
 [out] Restituisce il numero di tipi scritti, oppure, se il `types` parametro è `NULL`, quindi il numero totale dei tipi disponibili.  
  
 `types[]`  
 [out] Matrice che deve essere compilato con il [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) gli oggetti che rappresentano tutti i tipi per questo simbolo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
