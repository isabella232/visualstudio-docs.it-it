---
title: Symsareequiv | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c27cc4b984b250e70ba44122067df0bbfb4dc86
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885800"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verifica se due simboli sono equivalenti.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `symbolA`  
 [in] Il primo [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto utilizzato nel confronto.  
  
 `symbolB`  
 [in] Il secondo `IDiaSymbol` oggetto utilizzato nel confronto.  
  
## <a name="return-value"></a>Valore restituito  
 Se i simboli sono equivalenti, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`, i simboli non sono equivalenti. In caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



