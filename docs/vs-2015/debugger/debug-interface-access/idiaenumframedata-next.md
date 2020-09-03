---
title: IDiaEnumFrameData::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe8735511e9830542ce8622a6d984a0a817671
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161223"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un numero specificato di elementi dati del frame nella sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 in Numero di elementi dati del frame nell'enumeratore da recuperare.  
  
 rgelt  
 out Matrice di oggetti [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) da compilare con gli elementi dati del frame richiesti.  
  
 pceltFetched  
 out Restituisce il numero di elementi dati del frame nell'enumeratore recuperato.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri record. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
