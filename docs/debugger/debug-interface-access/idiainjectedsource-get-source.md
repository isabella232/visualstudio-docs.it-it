---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b5582990ff3db2e03dce9dc0c198a907de978d9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971075"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Recupera i byte del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Il numero di byte che rappresenta le dimensioni del buffer di dati.  
  
 `pcbData`  
 [out] Restituisce il numero di byte che rappresenta i byte. Se `data` viene `NULL`, quindi `pcbData` è il numero totale di byte di dati disponibili.  
  
 `data[]`  
 [out] Un buffer che deve essere compilato con i byte di origine.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)