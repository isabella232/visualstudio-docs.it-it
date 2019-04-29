---
title: IDiaSectionContrib::get_dataCrc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_dataCrc method
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 309ecc0269b911afb1f8e1b753811ac0b1c36e6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576548"
---
# <a name="idiasectioncontribgetdatacrc"></a>IDiaSectionContrib::get_dataCrc
Recupera il controllo di ridondanza ciclico (CRC) dei dati nella sezione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_dataCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il CRC dei dati nella sezione.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)