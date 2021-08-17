---
description: Recupera i byte di checksum.
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6c816fd0e44ee4870bbc656aa48621b175908692
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058874"
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

[in] Dimensioni del buffer di dati, in byte.

 `pcbData`

[out] Restituisce il numero di byte di checksum. Questo parametro non può essere `NULL`.

 `data`

[in, out] Buffer riempito con i byte di checksum. Se questo parametro è `NULL` , restituisce il numero di byte `pcbData` necessari.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per determinare il tipo di algoritmo di checksum usato per generare i byte di checksum, chiamare il metodo [IDiaSourceFile::get_checksumType.](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)

 Il checksum viene in genere generato dall'immagine del file di origine in modo che le modifiche apportate al file di origine si riflettano nelle modifiche nei byte del checksum. Se i byte di checksum non corrispondono a un checksum generato dall'immagine caricata del file, il file deve essere considerato danneggiato o manomesso.

 I checksum tipici non hanno mai dimensioni superiori a 32 byte, ma non presuppongono che sia la dimensione massima di un checksum. Impostare il `data` parametro su per ottenere il numero di byte necessari per recuperare il `NULL` checksum. Allocare quindi un buffer delle dimensioni appropriate e chiamare ancora una volta questo metodo con il nuovo buffer.

## <a name="see-also"></a>Vedi anche
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
