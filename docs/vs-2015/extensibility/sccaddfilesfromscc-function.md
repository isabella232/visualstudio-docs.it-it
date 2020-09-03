---
title: Funzione SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200917"
---
# <a name="sccaddfilesfromscc-function"></a>Funzione SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione aggiunge un elenco di file dal controllo del codice sorgente al progetto attualmente aperto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pContext  
 in Puntatore al contesto del plug-in del controllo del codice sorgente.  
  
 hWnd  
 in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.  
  
 lpUser  
 [in, out] Nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione null).  
  
 lpAuxProjPath  
 [in, out] Stringa ausiliaria che identifica il progetto (fino alla `SCC_PRJPATH_` dimensione, incluso il carattere di terminazione null).  
  
 cFiles  
 in Numero di file specificati da `lpFilePaths` .  
  
 lpFilePaths  
 [in, out] Matrice di nomi di file da aggiungere al progetto corrente.  
  
 lpDestination  
 in Percorso di destinazione in cui devono essere scritti i file.  
  
 lpComment  
 in Commento da applicare a ognuno dei file aggiunti.  
  
 pbResults  
 [in, out] Matrice di flag impostati per indicare l'esito positivo (valore diverso da zero o TRUE) o errore (zero o FALSE) per ogni file (la dimensione della matrice deve essere almeno `cFiles` Long).  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Il progetto non è aperto.|  
|SCC_E_OPNOTPERFORMED|La connessione non è allo stesso progetto specificata da `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato ad aggiornare il database.|  
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|  
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
