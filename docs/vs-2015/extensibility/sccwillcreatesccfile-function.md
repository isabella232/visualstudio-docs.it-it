---
title: Funzione SccWillCreateSccFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147957"
---
# <a name="sccwillcreatesccfile-function"></a>Funzione SccWillCreateSccFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione determina se il plug-in del controllo del codice sorgente supporta la creazione di MSSCCPRJ. File SCC per ognuno dei file specificati.  
  
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
 in Puntatore al contesto del plug-in del controllo del codice sorgente.  
  
 nFile  
 in Il numero di nomi di file inclusi nella `lpFileNames` matrice e la lunghezza della `pbSccFiles` matrice.  
  
 lpFileNames  
 in Matrice di nomi di file completi da controllare (la matrice deve essere allocata dal chiamante).  
  
 pbSccFiles  
 [in, out] Matrice in cui archiviare i risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Esito positivo.|  
|SCC_E_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione viene chiamata con un elenco di file per determinare se il plug-in del controllo del codice sorgente fornisce supporto in MSSCCPRJ. File SCC per ognuno dei file specificati (per altre informazioni su MSSCCPRJ. File SCC, vedere [Mssccprj. File SCC](../extensibility/mssccprj-scc-file.md)). I plug-in del controllo del codice sorgente possono dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug-in restituisce `TRUE` o `FALSE` per file nella `pbSccFiles` matrice per indicare quale dei file specificati dispone di Mssccprj. Supporto SCC. Se il plug-in restituisce un codice di riuscita dalla funzione, i valori nella matrice restituita vengono rispettati. In caso di errore, la matrice viene ignorata.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
