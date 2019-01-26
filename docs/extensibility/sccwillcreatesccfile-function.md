---
title: Funzione SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b629b83aa329a4a3e25197236e33ee152e378472
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937207"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
Questa funzione determina se il controllo del codice sorgente del plug-in supporta la creazione del MSSCCPRJ. File di controllo del codice sorgente per ogni file specificati.  
  
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
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 nFiles  
 [in] Il numero di nomi di file inclusi nel `lpFileNames` matrice, nonché la lunghezza del `pbSccFiles` matrice.  
  
 lpFileNames  
 [in] Una matrice di nomi di file completo per verificare (matrice deve essere allocata dal chiamante).  
  
 pbSccFiles  
 [in, out] Matrice in cui archiviare i risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione completata.|  
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce il supporto nel MSSCCPRJ. File di controllo del codice sorgente per ogni file specifici (per ulteriori informazioni sul MSSCCPRJ. File di controllo del codice sorgente, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)). Plug-in controllo codice sorgente può dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` oppure `FALSE` per ogni file nei `pbSccFiles` matrice per indicare che il file specificato hanno MSSCCPRJ. Supporto di SCC. Se il plug-in restituisce un codice di riuscita dalla funzione, vengono rispettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)