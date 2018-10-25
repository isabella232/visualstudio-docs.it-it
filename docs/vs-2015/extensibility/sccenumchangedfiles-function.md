---
title: Funzione SccEnumChangedFiles | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16bc3c17fbf7d9d11951dcbe670c8c7edba66364
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860079"
---
# <a name="sccenumchangedfiles-function"></a>Funzione SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
#### <a name="parameters"></a>Parametri  
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
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)

