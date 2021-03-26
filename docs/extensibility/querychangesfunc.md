---
title: QUERYCHANGESFUNC | Microsoft Docs
description: La funzione di callback QUERYCHANGESFUNC viene utilizzata per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc797d68f6df6d9aab93554ba95955a7d9f45eea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068622"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Si tratta di una funzione di callback utilizzata dall'operazione [SccQueryChanges](../extensibility/sccquerychanges-function.md) per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.

 Alla `SccQueryChanges` funzione viene assegnato un elenco di file e un puntatore al `QUERYCHANGESFUNC` callback. Il plug-in del controllo del codice sorgente enumera l'elenco specificato e fornisce lo stato (tramite questo callback) per ogni file nell'elenco.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

in Il `pvCallerData` parametro passato dal chiamante (IDE) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). Il plug-in del controllo del codice sorgente non deve fare supposizioni sul contenuto di questo valore.

 pChangesData

in Puntatore a una struttura di [struttura QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) che descrive le modifiche apportate a un file.

## <a name="return-value"></a>Valore restituito
 L'IDE restituisce un codice di errore appropriato:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Consente di arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore SCC appropriato interrompe l'elaborazione.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Struttura QUERYCHANGESDATA
 La struttura passata per ogni file ha un aspetto simile al seguente:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 Dimensioni dwSize della struttura (in byte).

 lpFileName il nome del file originale per questo elemento.

 Codice dwChangeType che indica lo stato del file:

|Codice|Descrizione|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Impossibile stabilire cosa è stato modificato.|
|`SCC_CHANGE_UNCHANGED`|Non sono state apportate modifiche al nome del file.|
|`SCC_CHANGE_DIFFERENT`|File con un'identità diversa, ma lo stesso nome esiste nel database.|
|`SCC_CHANGE_NONEXISTENT`|Il file non esiste nel database o in locale.|
|`SCC_CHANGE_DATABASE_DELETED`|File eliminato nel database.|
|`SCC_CHANGE_LOCAL_DELETED`|Il file è stato eliminato localmente, ma il file esiste ancora nel database. Se non è possibile determinare questo, restituire `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Il file è stato aggiunto al database ma non esiste localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|Il file non esiste nel database ed è un nuovo file locale.|
|`SCC_CHANGE_RENAMED_TO`|Il file è stato rinominato o spostato nel database come `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Il file è stato rinominato o spostato nel database da `lpLatestName` ; se la traccia è troppo costosa, restituire un flag diverso, ad esempio `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName il nome del file corrente per questo elemento.

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Codici di errore](../extensibility/error-codes.md)
