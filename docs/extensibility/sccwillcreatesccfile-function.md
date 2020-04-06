---
title: SccWillCreateSccFile (funzione) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700206"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
Questa funzione determina se il plug-in del controllo del codice sorgente supporta la creazione di MSSCCPRJ. SCC per ciascuno dei file dati.

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

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 nFile

[in] Il numero di nomi `lpFileNames` di file inclusi nella `pbSccFiles` matrice e la lunghezza della matrice.

 LpNomidi File

[in] Matrice di nomi di file completi da controllare (la matrice deve essere allocata dal chiamante).

 pbSccFiles (file pbScc)

[in, out] Matrice in cui archiviare i risultati.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo.|
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce supporto in MSSCCPRJ. SCC per ciascuno dei file dati (per ulteriori informazioni su MSSCCPRJ. SCC, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)). I plug-in del controllo del codice sorgente possono dichiarare se sono in grado di creare MSSCCPRJ. SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in `TRUE` `FALSE` restituisce o `pbSccFiles` per file nell'array per indicare quale dei file specificato dispone di MSSCCPRJ. Supporto SCC. Se il plug-in restituisce un codice di esito positivo dalla funzione, i valori nella matrice restituita vengono rispettati. In caso di errore, la matrice viene ignorata.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
