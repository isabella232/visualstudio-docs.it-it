---
title: IDiaEnumSectionContribs::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::get__NewEnum method
ms.assetid: a16ee92f-3081-416a-98f6-ce6bc8288a8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bbd4e2d818fe2e795b03536b514297a05771e92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744305"
---
# <a name="idiaenumsectioncontribsget__newenum"></a>IDiaEnumSectionContribs::get__NewEnum
Recupera la versione <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> dell'enumeratore.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce l'interfaccia `IUnknown` che rappresenta la versione <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> dell'enumeratore.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)