---
title: Proprietà QUERYCHANGESFUNC . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701639"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Si tratta di una funzione di callback utilizzata dall'operazione [SccQueryChanges](../extensibility/sccquerychanges-function.md) per enumerare una raccolta di nomi di file e determinare lo stato di ogni file.

 Alla `SccQueryChanges` funzione viene fornito un elenco di `QUERYCHANGESFUNC` file e un puntatore al callback. Il plug-in del controllo del codice sorgente enumera l'elenco specificato e fornisce lo stato (tramite questo callback) per ogni file nell'elenco.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parametri
 pvCallerData (informazioni in fibra con i dati)

[in] Il `pvCallerData` parametro passato dal chiamante (l'IDE) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). Il plug-in del controllo del codice sorgente non deve fare supposizioni sul contenuto di questo valore.

 pChangesData (dati di base)

[in] Puntatore a una struttura [QUERYCHANGESDATA che](#LinkQUERYCHANGESDATA) descrive le modifiche apportate a un file.

## <a name="return-value"></a>Valore restituito
 L'IDE restituisce un codice di errore appropriato:The IDE returns an appropriate error code:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Continuare l'elaborazione.|
|SCC_I_OPERATIONCANCELED|Consente di arrestare l'elaborazione.|
|SCC_E_xxx|Qualsiasi errore SCC appropriato dovrebbe interrompere l'elaborazione.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>Struttura QUERYCHANGESDATA
 La struttura passata per ogni file è simile alla seguente:The structure passed in for each file looks like the following:

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

 dwSize Dimensione di questa struttura (in byte).

 lpFileName Il nome del file originale per l'elemento.

 dwChangeType Codice che indica lo stato del file:

|Codice|Descrizione|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Non riesco a capire cosa è cambiato.|
|`SCC_CHANGE_UNCHANGED`|Nessuna modifica del nome per questo file.|
|`SCC_CHANGE_DIFFERENT`|File con un'identità diversa, ma lo stesso nome esiste nel database.|
|`SCC_CHANGE_NONEXISTENT`|Il file non esiste nel database o in locale.|
|`SCC_CHANGE_DATABASE_DELETED`|File eliminato nel database.|
|`SCC_CHANGE_LOCAL_DELETED`|File eliminato localmente, ma il file esiste ancora nel database. Se non è possibile `SCC_CHANGE_DATABASE_ADDED`determinarlo, restituire .|
|`SCC_CHANGE_DATABASE_ADDED`|File aggiunto al database ma non esistente localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|Il file non esiste nel database ed è un nuovo file locale.|
|`SCC_CHANGE_RENAMED_TO`|File rinominato o spostato `lpLatestName`nel database come .|
|`SCC_CHANGE_RENAMED_FROM`|File rinominato o spostato `lpLatestName`nel database da ; se questa operazione è troppo costosa da monitorare, restituire un flag diverso, ad `SCC_CHANGE_DATABASE_ADDED`esempio .|

 lpLatestName Il nome del file corrente per questo elemento.

## <a name="see-also"></a>Vedere anche
- [Callback functions implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Codici di errore](../extensibility/error-codes.md)
