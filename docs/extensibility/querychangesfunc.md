---
title: QueryCHANGESFUNC | Microsoft Docs
description: La funzione di callback QUERYCHANGESFUNC viene usata per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b061fbfb6644f77348574020c0a5cb614691ae6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899134"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Si tratta di una funzione di callback usata [dall'operazione SccQueryChanges](../extensibility/sccquerychanges-function.md) per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.

 Alla `SccQueryChanges` funzione viene fornito un elenco di file e un puntatore al `QUERYCHANGESFUNC` callback. Il plug-in del controllo del codice sorgente enumera l'elenco specificato e fornisce lo stato (tramite questo callback) per ogni file nell'elenco.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

[in] Parametro `pvCallerData` passato dal chiamante (IDE) a [SccQueryChanges.](../extensibility/sccquerychanges-function.md) Il plug-in del controllo del codice sorgente non deve fare supposizioni sul contenuto di questo valore.

 pChangesData

[in] Puntatore a una [struttura QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) che descrive le modifiche apportate a un file.

## <a name="return-value"></a>Valore restituito
 L'IDE restituisce un codice di errore appropriato:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Consente di arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore SCC appropriato deve interrompere l'elaborazione.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Struttura QUERYCHANGESDATA
 La struttura passata per ogni file è simile alla seguente:

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

 dwSize Dimensione della struttura (in byte).

 lpFileName Nome del file originale per questo elemento.

 Codice dwChangeType che indica lo stato del file:

|Codice|Descrizione|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Non è possibile indicare cosa è stato modificato.|
|`SCC_CHANGE_UNCHANGED`|Nessun nome modificato per questo file.|
|`SCC_CHANGE_DIFFERENT`|File con un'identità diversa, ma lo stesso nome esiste nel database.|
|`SCC_CHANGE_NONEXISTENT`|Il file non esiste nel database o in locale.|
|`SCC_CHANGE_DATABASE_DELETED`|File eliminato nel database.|
|`SCC_CHANGE_LOCAL_DELETED`|Il file è stato eliminato in locale, ma il file esiste ancora nel database. Se non è possibile determinare questo valore, restituire `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Il file è stato aggiunto al database ma non esiste in locale.|
|`SCC_CHANGE_LOCAL_ADDED`|Il file non esiste nel database ed è un nuovo file locale.|
|`SCC_CHANGE_RENAMED_TO`|File rinominato o spostato nel database come `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|File rinominato o spostato nel database da . Se è troppo costoso da `lpLatestName` rilevare, restituire un flag diverso, ad esempio `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName Nome del file corrente per questo elemento.

## <a name="see-also"></a>Vedere anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Codici di errore](../extensibility/error-codes.md)
