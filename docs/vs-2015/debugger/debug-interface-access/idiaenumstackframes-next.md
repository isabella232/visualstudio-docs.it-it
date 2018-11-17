---
title: Idiaenumstackframes | Microsoft Docs
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
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aaaf66da29711a279111c1f7d63ca285dc779596
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726475"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un numero specificato di elementi dello stack frame dalla sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di elementi di stack frame nell'enumeratore deve essere recuperato.  
  
 rgelt  
 [out] Matrice che deve essere compilata con l'oggetto richiesto [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) oggetti.  
  
 pceltFetched  
 [out] Restituisce il numero di stack frame elementi nell'enumeratore recuperata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se sono presenti più stack frame. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



