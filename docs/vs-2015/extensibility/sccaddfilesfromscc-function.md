---
title: Funzione SccAddFilesFromSCC | Microsoft Docs
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
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 537ec62d6bd504a588a70931a7c66e20989fd9f2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805596"
---
# <a name="sccaddfilesfromscc-function"></a>Funzione SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione consente di aggiungere un elenco di file dal controllo del codice sorgente al progetto attualmente aperto.  
  
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
 [in] Il puntatore di contesto del plug-in controllo di origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione null).  
  
 lpAuxProjPath  
 [in, out] Stringa ausiliario che identifica il progetto (fino a `SCC_PRJPATH_`dimensione, incluso il carattere di terminazione null).  
  
 cFiles  
 [in] Numero di file specificato da `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Matrice di nomi di file da aggiungere al progetto corrente.  
  
 lpDestination  
 [in] Il percorso di destinazione in cui devono essere scritti i file.  
  
 lpComment  
 [in] Il commento da applicare a ogni file da aggiungere.  
  
 pbResults  
 [in, out] Matrice di flag di set per indicare l'esito positivo (diverso da zero o TRUE) o negativo (zero o FALSE) per ogni file (dimensione della matrice deve essere almeno `cFiles` long).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Progetto non è aperto.|  
|SCC_E_OPNOTPERFORMED|La connessione non è presente nello stesso progetto come specificato da `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Utente non è autorizzato ad aggiornare il database.|  
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)

