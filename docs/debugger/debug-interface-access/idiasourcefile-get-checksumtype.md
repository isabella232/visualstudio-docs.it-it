---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88a192c9328d37447f12226a3d564ecae58fe41f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465321"
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

out Restituisce il tipo di checksum.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il tipo di checksum è un valore di cui è possibile eseguire il mapping a un algoritmo di checksum. Ad esempio, il formato di file PDB standard può in genere avere uno dei valori seguenti:

|Tipo di checksum|Etichetta CryptoAPI|Descrizione|
|-------------------|---------------------|-----------------|
|0|\<none>|Nessun checksum presente.|
|1|`CALG_MD5`|checksum generato con l'algoritmo hash MD5.|
|2|`CALG_SHA1`|checksum generato con l'algoritmo hash SHA1.|

 Le `CryptoAPI` etichette sono dall' `ALG_ID` enumerazione. Per ulteriori informazioni sugli algoritmi di hashing, consultare la `CryptoAPI` sezione di Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] .

 Per ottenere i byte di checksum effettivi per il file di origine, chiamare il metodo [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)