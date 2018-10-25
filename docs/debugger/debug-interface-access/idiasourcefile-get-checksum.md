---
title: Get_checksum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f0484fce6f5355361c0c5156cd3c7ad827775c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919429"
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
  
## <a name="remarks"></a>Note  
 Per determinare il tipo di algoritmo di checksum utilizzata per generare i byte di checksum, chiamare il [Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) (metodo).  
  
 Il valore di checksum viene solitamente generato dall'immagine del file di origine in modo che le modifiche nel file di origine vengono applicate le modifiche nei byte checksum. Se i byte di checksum non corrispondono a un checksum generato dall'immagine del file, caricare quindi il file deve essere considerato danneggiato o manomesso.  
  
 I tipici valori di checksum non sono mai più di 32 byte le dimensioni ma non presupporre che sia la dimensione massima di un checksum. Impostare il `data` parametro per `NULL` per ottenere il numero di byte necessari per recuperare il valore di checksum. Quindi allocare un buffer di dimensione appropriata e chiamare questo metodo, ancora una volta con il nuovo buffer.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)