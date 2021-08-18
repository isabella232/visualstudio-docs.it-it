---
description: Recupera il tipo di checksum.
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7ed2d914bbd8c35e8d6f33a3cfe504a0ba40f9f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066188"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Recupera il tipo di checksum.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il tipo di checksum.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il tipo di checksum è un valore di cui è possibile eseguire il mapping a un algoritmo di checksum. Ad esempio, il formato di file PDB standard può in genere avere uno dei valori seguenti:

|Tipo di checksum|Etichetta CryptoAPI|Descrizione|
|-------------------|---------------------|-----------------|
|0|\<none>|Nessun checksum presente.|
|1|`CALG_MD5`|checksum generato con l'algoritmo hash MD5.|
|2|`CALG_SHA1`|checksum generato con l'algoritmo hash SHA1.|

 Le `CryptoAPI` etichette derivano dall'enumerazione `ALG_ID` . Per altre informazioni sugli algoritmi di hash, vedere la `CryptoAPI` sezione di Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] .

 Per ottenere i byte di checksum effettivi per il file di origine, chiamare il [metodo IDiaSourceFile::get_checksum.](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)

## <a name="see-also"></a>Vedi anche
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
