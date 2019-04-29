---
title: Funzione SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fa85c8a96f17508d2e2e53a8d14444dd857dad0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800280"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
Questa funzione determina se il controllo del codice sorgente del plug-in supporta la creazione del MSSCCPRJ. File di controllo del codice sorgente per ogni file specificati.

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

[in] Il puntatore di contesto del plug-in controllo di origine.

 nFiles

[in] Il numero di nomi di file inclusi nel `lpFileNames` matrice, nonché la lunghezza del `pbSccFiles` matrice.

 lpFileNames

[in] Una matrice di nomi di file completo per verificare (matrice deve essere allocata dal chiamante).

 pbSccFiles

[in, out] Matrice in cui archiviare i risultati.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata.|
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce il supporto nel MSSCCPRJ. File di controllo del codice sorgente per ogni file specifici (per ulteriori informazioni sul MSSCCPRJ. File di controllo del codice sorgente, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)). Plug-in controllo codice sorgente può dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` oppure `FALSE` per ogni file nei `pbSccFiles` matrice per indicare che il file specificato hanno MSSCCPRJ. Supporto di SCC. Se il plug-in restituisce un codice di riuscita dalla funzione, vengono rispettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)