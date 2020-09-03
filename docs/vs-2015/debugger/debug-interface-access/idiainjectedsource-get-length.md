---
title: IDiaInjectedSource::get_length | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ce9a927f8e2e732bd5b74d0f58afa40a7cf8efa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192443"
---
# <a name="idiainjectedsourceget_length"></a>IDiaInjectedSource::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera il numero di byte di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 out Restituisce il numero di byte di codice.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore restituito da questo metodo è la lunghezza del codice sorgente ed è lo stesso valore restituito dal metodo [IDiaInjectedSource:: get_Source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)
