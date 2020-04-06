---
title: SccQueryInfo (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700485"
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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 nFile

[in] Numero di file `lpFileNames` specificati nella matrice `lpStatus` e lunghezza della matrice.

 LpNomidi File

[in] Matrice di nomi di file su cui eseguire la query.

 lpStatus (Stato

[in, out] Matrice in cui il plug-in del controllo del codice sorgente restituisce i flag di stato per ogni file. Per ulteriori informazioni, consultate [Codice di stato del file.](../extensibility/file-status-code-enumerator.md)

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Query riuscita.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema con l'accesso al sistema di controllo del codice sorgente, probabilmente causato da problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Se `lpFileName` è una stringa vuota, attualmente non sono disponibili informazioni sullo stato da aggiornare. In caso contrario, è il nome del percorso completo del file per il quale le informazioni sullo stato potrebbero essere state modificate.

 La matrice restituita può `SCC_STATUS_xxxx` essere una maschera di bit. Per ulteriori informazioni, consultate [Codice di stato del file.](../extensibility/file-status-code-enumerator.md) Un sistema di controllo del codice sorgente potrebbe non supportare tutti i tipi di bit. Ad esempio, `SCC_STATUS_OUTOFDATE` se non viene offerto, il bit non è impostato.

 Quando si utilizza questa funzione per `MSSCCI` estrarre i file, tenere presente i seguenti requisiti di stato:

- `SCC_STATUS_OUTBYUSER`viene impostato quando l'utente corrente ha estratto il file.

- `SCC_STATUS_CHECKEDOUT`non può `SCC_STATUS_OUTBYUSER` essere impostato a meno che non sia impostato.

- `SCC_STATUS_CHECKEDOUT`viene impostato solo quando il file è estratto nella directory di lavoro designata.

- Se il file è estratto dall'utente corrente in una `SCC_STATUS_OUTBYUSER` directory diversa `SCC_STATUS_CHECKEDOUT` da quella di lavoro, è impostata ma non lo è.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)
