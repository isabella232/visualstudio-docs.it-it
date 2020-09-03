---
title: Funzione SccEnumChangedFiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200124"
---
# <a name="sccenumchangedfiles-function"></a>Funzione SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
#### <a name="parameters"></a>Parametri  
 pContext  
 in Puntatore al contesto del plug-in del controllo del codice sorgente.  
  
 hWnd  
 in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.  
  
 cFiles  
 in Numero di nomi di file specificati nella `lpFileNames` matrice. Specifica anche la dimensione della `plIsFileDifferent` matrice.  
  
 lpFileNames  
 in Matrice di nomi di file locali da verificare.  
  
 plIsFileDifferent  
 [in, out] Matrice di valori che indica lo stato della differenza di ogni file (la matrice deve contenere almeno `cFiles` voci). Diverso da zero indica che il file è diverso.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata correttamente.|  
|SCC_UNSPECIFIEDERROR|Errore generico.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
