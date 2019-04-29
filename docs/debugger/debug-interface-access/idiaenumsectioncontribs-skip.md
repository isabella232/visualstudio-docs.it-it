---
title: Idiaenumsectioncontribs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c90c2148fc5a563fef8946bd39acf4603d7d09f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833233"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Ignora un determinato numero di contributi di sezione in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 `celt`

[in] Il numero dei contributi di sezione nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se non esistono Nessun più contributi di sezione da ignorare.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)