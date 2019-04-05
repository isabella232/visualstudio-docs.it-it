---
title: IDiaEnumSymbols::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42180b8e948b93428dc2db92820be336833dcc56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966460"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un simbolo mediante un indice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 indice  
 [in] Indice del [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto da recuperare. L'indice è compreso nell'intervallo da 0 a `count`-1, dove `count` restituito dalle [Idiaenumsymbols](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) (metodo).  
  
 simbolo  
 [out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il simbolo desiderato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
