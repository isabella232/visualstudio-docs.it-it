---
description: Recupera il nome file per l'ultimo errore di caricamento.
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1a15333df3c4c994f752ff7bd93978a7b7e34ffb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036575"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Recupera il nome file per l'ultimo errore di caricamento.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce una stringa che contiene il nome del file con estensione pdb associato all'ultimo errore di caricamento.

## <a name="return-value"></a>Valore restituito
 Restituisce l'ultimo codice di errore causato da un'operazione di caricamento. Restituisce `E_INVALIDARG` se il parametro è `pRetVal` `NULL` .

## <a name="example"></a>Esempio

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
