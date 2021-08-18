---
description: Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 71948d51865e82f3dd0fa2fe7bb29fd200b59f30
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129055"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Legge il numero specificato di byte a partire dall'offset specificato da un file eseguibile.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametri
 fileOffset

[in] Offset nel file eseguibile da iniziare la lettura.

 cbData

[in] Numero di byte da leggere.

 pcbData

[out] Restituisce il numero di byte letti.

 data[]

[in, out] Matrice compilata con i byte letti dal file.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato dal codice di supporto DIA per caricare i byte di dati da un eseguibile usando un offset di file assoluto. Questo metodo viene chiamato a supporto del [metodo IDiaDataSource::loadDataForExe.](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

## <a name="see-also"></a>Vedi anche
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
