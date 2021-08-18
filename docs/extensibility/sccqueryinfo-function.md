---
description: Questa funzione ottiene informazioni sullo stato per un set di file selezionati nel controllo del codice sorgente.
title: Funzione SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7b61a5cfd52bfbeadf2b11212bd3f215390d2d4d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110007"
---
# <a name="sccqueryinfo-function"></a>Funzione SccQueryInfo
Questa funzione ottiene informazioni sullo stato per un set di file selezionati nel controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 nFiles

[in] Numero di file specificati nella `lpFileNames` matrice e la lunghezza della `lpStatus` matrice.

 lpFileNames

[in] Matrice di nomi di file su cui eseguire la query.

 lpStatus

[in, out] Matrice in cui il plug-in del controllo del codice sorgente restituisce i flag di stato per ogni file. Per altre informazioni, vedere [Codice di stato del file.](../extensibility/file-status-code-enumerator.md)

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La query ha avuto esito positivo.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema con l'accesso al sistema di controllo del codice sorgente, probabilmente causato da problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Se `lpFileName` è una stringa vuota, attualmente non sono disponibili informazioni sullo stato da aggiornare. In caso contrario, è il nome del percorso completo del file per il quale potrebbero essere state modificate le informazioni sullo stato.

 La matrice restituita può essere una maschera di `SCC_STATUS_xxxx` bit di bit. Per altre informazioni, vedere [Codice di stato del file.](../extensibility/file-status-code-enumerator.md) Un sistema di controllo del codice sorgente potrebbe non supportare tutti i tipi di bit. Ad esempio, se `SCC_STATUS_OUTOFDATE` non viene offerto, il bit non è impostato.

 Quando si usa questa funzione per estrarre i file, tenere presente i requisiti `MSSCCI` di stato seguenti:

- `SCC_STATUS_OUTBYUSER` viene impostato quando l'utente corrente ha estratto il file.

- `SCC_STATUS_CHECKEDOUT` non può essere impostato a meno che `SCC_STATUS_OUTBYUSER` non sia impostato .

- `SCC_STATUS_CHECKEDOUT` viene impostato solo quando il file viene estratto nella directory di lavoro designata.

- Se il file viene estratto dall'utente corrente in una directory diversa dalla directory di lavoro, viene `SCC_STATUS_OUTBYUSER` impostato ma non lo `SCC_STATUS_CHECKEDOUT` è.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)
