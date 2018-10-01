---
title: Funzione SccEnumChangedFiles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 4d1935724a965d7b7d62e6bc059c0d483bb3a1b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529369"
---
# <a name="sccenumchangedfiles-function"></a>Funzione SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccEnumChangedFiles](https://docs.microsoft.com/visualstudio/extensibility/sccenumchangedfiles-function).  
  
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

