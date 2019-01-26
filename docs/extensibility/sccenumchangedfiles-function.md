---
title: Funzione SccEnumChangedFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94c672ddbd134f978e91bf6df06a902ca8a3fa4c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009947"
---
# <a name="sccenumchangedfiles-function"></a>Funzione SccEnumChangedFiles
Dato un elenco di file locali, questa funzione determina quali file sono diversi rispetto alle versioni corrispondenti nel database del controllo del codice sorgente.  
  
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
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 cFiles  
 [in] Numero di nomi di file specificato nella `lpFileNames` matrice. Specifica anche dimensioni di `plIsFileDifferent` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file locali da controllare.  
  
 plIsFileDifferent  
 [in, out] Matrice di valori che indicano lo stato di differenza di ogni file (matrice deve avere almeno `cFiles` voci). Diverso da zero indica che il file è diverso.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata correttamente.|  
|SCC_UNSPECIFIEDERROR|Errore generico.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)