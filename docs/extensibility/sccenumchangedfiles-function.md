---
title: SccEnumChangedFiles (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700911"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles (funzione)SccEnumChangedFiles function
Dato un elenco di file locali, questa funzione determina quali file sono diversi dalle versioni corrispondenti nel database del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 CFile (File)

[in] Numero di nomi di `lpFileNames` file specificati nella matrice. Specifica anche la `plIsFileDifferent` dimensione della matrice.

 LpNomidi File

[in] Matrice di nomi di file locali da controllare.

 plIsFileDifferent

[in, out] Matrice di valori che indicano lo stato di `cFiles` differenza di ogni file (array deve avere almeno voci). Diverso da zero significa che il file è diverso.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata correttamente.|
|SCC_UNSPECIFIEDERROR|Errore generico.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
