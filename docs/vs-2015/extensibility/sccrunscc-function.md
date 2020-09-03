---
title: Funzione SccRunScc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b36bd226d4eb19a694347edcba51812ee6f771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190876"
---
# <a name="sccrunscc-function"></a>Funzione SccRunScc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione richiama lo strumento di amministrazione del controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 in Struttura del contesto del plug-in del controllo del codice sorgente.  
  
 hWnd  
 in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.  
  
 nFile  
 in Numero di file specificati nella `lpFileNames` matrice.  
  
 lpFileNames  
 in Matrice dei nomi file selezionati.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Lo strumento di amministrazione del controllo del codice sorgente è stato richiamato correttamente.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema di controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto.|  
|SCC_E_CONNECTIONFAILURE|Non è stato possibile connettersi al sistema di controllo del codice sorgente.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione consente al chiamante di accedere all'intera gamma di funzionalità del sistema di controllo del codice sorgente tramite uno strumento di amministrazione esterno. Se il sistema di controllo del codice sorgente non dispone di un'interfaccia utente, il plug-in del controllo del codice sorgente può implementare un'interfaccia per eseguire le funzioni di amministrazione necessarie.  
  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi file per i file attualmente selezionati. Se lo strumento di amministrazione lo supporta, è possibile utilizzare l'elenco dei file per preselezionare i file nell'interfaccia di amministrazione. in caso contrario, l'elenco può essere ignorato.  
  
 Questa funzione viene in genere richiamata quando l'utente seleziona l' ** \<Source Control Server> avvio** dal menu del controllo del **File**  ->  **codice sorgente** del file. Questa opzione di menu di **avvio** può essere sempre disabilitata o anche nascosta impostando una voce del registro di sistema. Per informazioni dettagliate, vedere [procedura: installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md) . Questa funzione viene chiamata solo se [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il `SCC_CAP_RUNSCC` bit di capacità (vedere [flag funzionalità](../extensibility/capability-flags.md) per informazioni dettagliate su questo e altri bit di funzionalità).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Procedura: installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Flag funzionalità](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
