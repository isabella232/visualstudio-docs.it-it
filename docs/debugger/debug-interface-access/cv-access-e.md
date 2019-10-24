---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745365"
---
# <a name="cv_access_e"></a>CV_access_e
Specifica l'ambito di visibilità (livello di accesso) delle variabili e delle funzioni membro.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementi
Il membro CV_private dispone di accesso privato.

Il membro CV_protected ha accesso protetto.

Il membro CV_public dispone di accesso pubblico.

## <a name="remarks"></a>Note
L'identificatore di accesso `friend` non è incluso in questo argomento perché viene in genere usato da funzioni non membro che hanno accesso agli elementi privati e protetti della classe. Usare il metodo [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) per trovare i simboli con accesso `SymTagFriend`.

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
