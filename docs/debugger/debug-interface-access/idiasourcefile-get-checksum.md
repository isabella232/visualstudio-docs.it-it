---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f02338f46ace5da0d7769a6b27bc3500b797a9be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977655"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Recupera i byte di checksum.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cbData`  
 [in] Dimensioni del buffer di dati, in byte.  
  
 `pcbData`  
 [out] Restituisce il numero di byte di checksum. Questo parametro non può essere `NULL`.  
  
 `data`  
 [in, out] Un buffer che viene riempito con i byte di checksum. Se questo parametro è `NULL`, quindi `pcbData` restituisce il numero di byte necessari.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Per determinare il tipo di algoritmo di checksum utilizzata per generare i byte di checksum, chiamare il [Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) (metodo).  
  
 Il valore di checksum viene solitamente generato dall'immagine del file di origine in modo che le modifiche nel file di origine vengono applicate le modifiche nei byte checksum. Se i byte di checksum non corrispondono a un checksum generato dall'immagine del file, caricare quindi il file deve essere considerato danneggiato o manomesso.  
  
 I tipici valori di checksum non sono mai più di 32 byte le dimensioni ma non presupporre che sia la dimensione massima di un checksum. Impostare il `data` parametro per `NULL` per ottenere il numero di byte necessari per recuperare il valore di checksum. Quindi allocare un buffer di dimensione appropriata e chiamare questo metodo, ancora una volta con il nuovo buffer.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)