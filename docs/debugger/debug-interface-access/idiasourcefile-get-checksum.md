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
ms.openlocfilehash: 8f4367a7862dabe248dfbe08e64c45598abe3679
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741838"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
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

in Dimensioni in byte del buffer di dati.

 `pcbData`

out Restituisce il numero di byte di checksum. Questo parametro non può essere `NULL`.

 `data`

[in, out] Buffer riempito con i byte di checksum. Se questo parametro è `NULL`, `pcbData` restituisce il numero di byte necessari.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Per determinare il tipo di algoritmo di checksum utilizzato per generare i byte di checksum, chiamare il metodo [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .

 Il checksum viene in genere generato dall'immagine del file di origine in modo che le modifiche apportate al file di origine vengano riflesse nelle modifiche dei byte di checksum. Se i byte di checksum non corrispondono a un checksum generato dall'immagine caricata del file, il file deve essere considerato danneggiato o manomesso.

 I checksum tipici non sono mai di dimensioni superiori a 32 byte, ma non presuppongono che sia la dimensione massima di un checksum. Impostare il parametro `data` su `NULL` per ottenere il numero di byte necessari per recuperare il checksum. Allocare quindi un buffer delle dimensioni appropriate e chiamare questo metodo una volta al nuovo buffer.

## <a name="see-also"></a>Vedere anche
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)