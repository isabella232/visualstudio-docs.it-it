---
description: Recupera un flag che indica se la sezione è un record COMDAT.
title: IDiaSectionContrib::get_comdat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: abf3d900714d94dc051cca2b601cf041820de865
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629459"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
Recupera un flag che indica se la sezione è un record COMDAT.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se la sezione è un record COMDAT; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Un record COMDAT è un record COFF (Common Object File Format) che rende visibili al linker le funzioni in pacchetto.

## <a name="see-also"></a>Vedi anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
