---
title: Funzione SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ac7657258b79b2e53bee8138bc5b2728f618eac
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720111"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
Questa funzione determina se il plug-in del controllo del codice sorgente supporta la creazione di MSSCCPRJ. File SCC per ognuno dei file specificati.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parametri
 pContext

in Puntatore al contesto del plug-in del controllo del codice sorgente.

 nFile

in Il numero di nomi di file inclusi nella matrice di `lpFileNames`, nonché la lunghezza della matrice di `pbSccFiles`.

 lpFileNames

in Matrice di nomi di file completi da controllare (la matrice deve essere allocata dal chiamante).

 pbSccFiles

[in, out] Matrice in cui archiviare i risultati.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata.|
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce supporto in MSSCCPRJ. File SCC per ognuno dei file specificati (per altre informazioni su MSSCCPRJ. File SCC, vedere [Mssccprj. File SCC](../extensibility/mssccprj-scc-file.md)). I plug-in del controllo del codice sorgente possono dichiarare se hanno la possibilità di creare MSSCCPRJ. I file SCC dichiarano `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` o `FALSE` per ogni file nella matrice `pbSccFiles` per indicare quale dei file specificati dispone di MSSCCPRJ. Supporto SCC. Se il plug-in restituisce un codice di riuscita dalla funzione, i valori nella matrice restituita vengono rispettati. In caso di errore, la matrice viene ignorata.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)