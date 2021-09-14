---
description: Recupera i contributi di sezione per mezzo di un indice.
title: IDiaEnumSectionContribs::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c18f39898347313784e6201aedbc02018771e6f5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630180"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
Recupera i contributi di sezione per mezzo di un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaSectionContrib** section
);
```

#### <a name="parameters"></a>Parametri
 index

[in] Indice [dell'oggetto IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) da recuperare. L'indice è compreso nell'intervallo da 0 a -1, dove viene restituito dal metodo `count` `count` [IDiaEnumSectionContribs::get_Count.](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)

 section

[out] Restituisce un [oggetto IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) che rappresenta il contributo di sezione desiderato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
