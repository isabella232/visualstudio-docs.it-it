---
description: Recupera un file di origine in base all'identificatore del file di origine.
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: df38c3d18f18f7c1c2bda021a8827fe76305c4c2cdd6fd2fce3e76269acf7c5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391856"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Recupera un file di origine in base all'identificatore del file di origine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametri
 `uniqueId`

[in] Specifica l'identificatore del file di origine.

 `ppResult`

[out] Restituisce un [oggetto IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) che rappresenta il file di origine recuperato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'identificatore del file di origine è un valore univoco usato internamente al DIA SDK per rendere univoci tutti i file di origine. Questo metodo viene in genere usato internamente al DIA SDK.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
