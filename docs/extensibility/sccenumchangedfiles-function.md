---
description: Dato un elenco di file locali, questa funzione determina quali file sono diversi dalle versioni corrispondenti nel database di controllo del codice sorgente.
title: Funzione SccEnumChangedFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8d1f2cac97ee883ddca7fec7a2f5d0725459c029
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158307"
---
# <a name="sccenumchangedfiles-function"></a>Funzione SccEnumChangedFiles
Dato un elenco di file locali, questa funzione determina quali file sono diversi dalle versioni corrispondenti nel database di controllo del codice sorgente.

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

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 cFiles

[in] Numero di nomi di file specificati nella `lpFileNames` matrice. Specifica anche le dimensioni della `plIsFileDifferent` matrice.

 lpFileNames

[in] Matrice di nomi di file locali da controllare.

 plIsFileDifferent

[in, out] Matrice di valori che indica lo stato della differenza di ogni file (la matrice deve avere `cFiles` almeno voci). Un valore diverso da zero indica che il file è diverso.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata correttamente.|
|SCC_UNSPECIFIEDERROR|Errore generico.|

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
