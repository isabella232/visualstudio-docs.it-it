---
title: Funzione SccRunScc | Microsoft Docs
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
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 67d2ad2ee783d23e3bd8c960ad5a94eac3fbd908
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733695"
---
# <a name="sccrunscc-function"></a>Funzione SccRunScc
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione richiama lo strumento di amministrazione di controllo di origine.  
  
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
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 nFile  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file selezionato.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Lo strumento di amministrazione di controllo di origine è stato richiamato.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_CONNECTIONFAILURE|Impossibile connettersi al sistema di controllo di origine.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione consente di accedere all'intera gamma di funzionalità del sistema di origine tramite uno strumento di amministrazione esterne al chiamante. Se il sistema di controllo di origine non dispone di alcuna interfaccia utente, il plug-in del controllo del codice sorgente può implementare un'interfaccia per eseguire funzioni amministrative necessarie.  
  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi di file per i file attualmente selezionati. Se lo strumento di amministrazione lo supporta, l'elenco dei file è utilizzabile per preselezionerà file nell'interfaccia di amministrazione; in caso contrario, l'elenco può essere ignorato.  
  
 Questa funzione viene richiamata in genere quando l'utente seleziona il **avvio veloce \<Source Control Server >** dal **File** -> **controllo del codice sorgente** menu di scelta. Ciò **avviare** opzione di menu può essere sempre disabilitata o persino nascosto impostando una voce del Registro di sistema. Visualizzare [procedura: installare un plug-in controllo origine](../extensibility/internals/how-to-install-a-source-control-plug-in.md) per informazioni dettagliate. Questa funzione viene chiamata solo se [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il `SCC_CAP_RUNSCC` bit funzionalità (vedere [flag funzionalità](../extensibility/capability-flags.md) per informazioni dettagliate su questo e gli altri bit funzionalità).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Procedura: installare un plug-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Flag funzionalità](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

