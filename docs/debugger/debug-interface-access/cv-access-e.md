---
title: CV_access_e | Microsoft Docs
description: Ottenere informazioni sul tipo CV_access_e di enumerazione, che specifica l'ambito di visibilità (livello di accesso) dei membri nell'SDK di accesso all'interfaccia di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f784380e1c96a28c200ee2f7ab70cfd21c40a343
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121763"
---
# <a name="cv_access_e"></a>CV_access_e
Specifica l'ambito di visibilità (livello di accesso) delle funzioni membro e delle variabili.

## <a name="syntax"></a>Sintassi

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementi
CV_private membro ha accesso privato.

CV_protected membro ha accesso protetto.

CV_public membro ha accesso pubblico.

## <a name="remarks"></a>Commenti
L'identificatore di accesso non è incluso qui perché viene in genere usato da funzioni non membro che hanno accesso agli elementi privati e `friend` protetti della classe. Usare il [metodo IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) per trovare i simboli con `SymTagFriend` accesso.

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
