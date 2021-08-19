---
description: Questa funzione determina se il plug-in del controllo del codice sorgente supporta la creazione di MSSCCPRJ. File SCC per ogni file specificato.
title: Funzione SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ef42e88426f5fa91fcebc5e8ffc1b0954c6554ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062602"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
Questa funzione determina se il plug-in del controllo del codice sorgente supporta la creazione di MSSCCPRJ. File SCC per ogni file specificato.

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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 nFile

[in] Numero di nomi di file inclusi nella `lpFileNames` matrice e lunghezza della `pbSccFiles` matrice.

 lpFileNames

[in] Matrice di nomi di file completi da controllare (la matrice deve essere allocata dal chiamante).

 pbSccFiles

[in, out] Matrice in cui archiviare i risultati.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata.|
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in di controllo del codice sorgente fornisce supporto in MSSCCPRJ. File SCC per ogni file specificato (per altre informazioni su MSSCCPRJ. SCC, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md). I plug-in del controllo del codice sorgente possono dichiarare se sono in grado di creare MSSCCPRJ. File SCC dichiarando durante `SCC_CAP_SCCFILE` l'inizializzazione. Il plug-in restituisce o per ogni file nella matrice per indicare quale dei `TRUE` `FALSE` file indicati ha `pbSccFiles` MSSCCPRJ. Supporto SCC. Se il plug-in restituisce un codice di esito positivo dalla funzione, vengono rispettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
