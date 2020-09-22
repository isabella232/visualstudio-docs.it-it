---
title: Funzione SccAdd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daac15bbb7829d510db17ba02057a2dc86c55990
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839475"
---
# <a name="sccadd-function"></a>Funzione SccAdd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione aggiunge nuovi file al sistema di controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 in Struttura del contesto del plug-in del controllo del codice sorgente.  
  
 hWnd  
 in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.  
  
 nFile  
 in Numero di file selezionati per essere aggiunti al progetto corrente come indicato nella `lpFileNames` matrice.  
  
 lpFileNames  
 in Matrice di nomi locali completi dei file da aggiungere.  
  
 lpComment  
 in Commento da applicare a tutti i file da aggiungere.  
  
 pfOptions  
 in Matrice di flag di comando, fornita in base ai singoli file.  
  
 pvOptions  
 in Opzioni specifiche del plug-in del controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione di aggiunta è stata completata.|  
|SCC_E_FILEALREADYEXISTS|Il file selezionato è già presente nel controllo del codice sorgente.|  
|SCC_E_TYPENOTSUPPORTED|Il tipo di file, ad esempio binario, non è supportato dal sistema di controllo del codice sorgente.|  
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. aggiunta non eseguita.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|  
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|  
  
## <a name="remarks"></a>Commenti  
 Il solito `fOptions` viene sostituito da una matrice, `pfOptions` , con una `LONG` specifica di opzione per ogni file. Questo perché il tipo di file può variare da file a file.  
  
> [!NOTE]
> Non è possibile specificare entrambe `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` le opzioni e per lo stesso file, ma è valido specificare nessuno dei due. L'impostazione di non è uguale all'impostazione `SCC_FILETYPE_AUTO` , nel qual caso il plug-in del controllo del codice sorgente rileva automaticamente il tipo di file.  
  
 Di seguito è riportato l'elenco dei flag usati nella `pfOptions` matrice:  
  
|Opzione|valore|Significato|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Il plug-in del controllo del codice sorgente deve rilevare il tipo di file.|  
|SCC_FILETYPE_TEXT|0x01|Indica un file di testo ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Indica un tipo di file diverso dal testo ASCII.|  
|SCC_ADD_STORELATEST|0x04|Archivia solo la copia più recente del file, senza Delta.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Considera il file come testo ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Considera il file come testo Unicode in formato UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Considera il file come testo Unicode nel formato UTF16 Little endian.|  
|SCC_FILETYPE_UTF16BE|0x40|Considera il file come testo Unicode nel formato UTF16 Big endian.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
