---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744979"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Recupera il nome del file per l'ultimo errore di caricamento.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce una stringa che contiene il nome del file con estensione pdb associato all'ultimo errore di caricamento.

## <a name="return-value"></a>Valore restituito
 Restituisce l'ultimo codice di errore causato da un'operazione di caricamento. Restituisce `E_INVALIDARG` se il `pRetVal` parametro è `NULL`.

## <a name="example"></a>Esempio

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)