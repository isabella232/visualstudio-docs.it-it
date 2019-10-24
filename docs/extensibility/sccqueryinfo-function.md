---
title: Funzione SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720835"
---
# <a name="sccqueryinfo-function"></a>Funzione SccQueryInfo
Questa funzione ottiene le informazioni sullo stato per un set di file selezionati nel controllo del codice sorgente.

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 nFile

in Numero di file specificati nella matrice di `lpFileNames` e lunghezza della matrice di `lpStatus`.

 lpFileNames

in Matrice di nomi di file su cui eseguire la query.

 lpStatus

[in, out] Matrice in cui il plug-in del controllo del codice sorgente restituisce i flag di stato per ogni file. Per ulteriori informazioni, vedere [codice di stato del file](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|La query è stata completata.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente causato da problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Se `lpFileName` è una stringa vuota, non sono attualmente disponibili informazioni sullo stato da aggiornare. In caso contrario, è il nome del percorso completo del file per il quale potrebbero essere state modificate le informazioni sullo stato.

 La matrice restituita può essere una maschera di bit di `SCC_STATUS_xxxx` bit. Per ulteriori informazioni, vedere [codice di stato del file](../extensibility/file-status-code-enumerator.md). Un sistema di controllo del codice sorgente potrebbe non supportare tutti i tipi di bit. Se, ad esempio, `SCC_STATUS_OUTOFDATE` non è disponibile, il bit non è impostato.

 Quando si usa questa funzione per estrarre i file, tenere presente i seguenti requisiti di stato `MSSCCI`:

- `SCC_STATUS_OUTBYUSER` viene impostato quando l'utente corrente ha estratto il file.

- non è possibile impostare `SCC_STATUS_CHECKEDOUT` a meno che non sia impostato `SCC_STATUS_OUTBYUSER`.

- `SCC_STATUS_CHECKEDOUT` viene impostato solo quando il file viene estratto nella directory di lavoro designata.

- Se il file viene estratto dall'utente corrente in una directory diversa dalla directory di lavoro, viene impostato `SCC_STATUS_OUTBYUSER` ma `SCC_STATUS_CHECKEDOUT` non lo è.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)