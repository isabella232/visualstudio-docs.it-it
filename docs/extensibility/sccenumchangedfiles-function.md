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
ms.openlocfilehash: 500d0072ffca6f0ada6d035aa59c60b8358a13aec9230077b64a724f5faf4747
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121273683"
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
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata correttamente.|
|SCC_UNSPECIFIEDERROR|Errore generico.|

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
