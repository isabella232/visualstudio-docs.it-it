---
title: Funzione SccWillCreateSccFile | Microsoft Docs
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
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb423e84073a945645948684d47532bcc354406c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891869"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione determina se il controllo del codice sorgente del plug-in supporta la creazione del MSSCCPRJ. File di controllo del codice sorgente per ogni file specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
 nFile  
 [in] Il numero di nomi di file inclusi nel `lpFileNames` matrice, nonché la lunghezza del `pbSccFiles` matrice.  
  
 lpFileNames  
 [in] Una matrice di nomi di file completo per verificare (matrice deve essere allocata dal chiamante).  
  
 pbSccFiles  
 [in, out] Matrice in cui archiviare i risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce il supporto nel MSSCCPRJ. File di controllo del codice sorgente per ogni file specifici (per ulteriori informazioni sul MSSCCPRJ. File di controllo del codice sorgente, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)). Plug-in controllo codice sorgente può dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` oppure `FALSE` per ogni file nei `pbSccFiles` matrice per indicare che il file specificato hanno MSSCCPRJ. Supporto di SCC. Se il plug-in restituisce un codice di riuscita dalla funzione, vengono rispettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)

