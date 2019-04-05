---
title: Funzione SccCheckin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964679"
---
# <a name="scccheckin-function"></a>Funzione SccCheckin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione controlla nei file precedentemente estratti al sistema di controllo di origine, le modifiche e la creazione di una nuova versione. Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da archiviare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file selezionati da archiviare.  
  
 lpFileNames  
 [in] Matrice di nomi di percorso locale completo di file da archiviare.  
  
 lpComment  
 [in] Commento da applicare a ogni file selezionati da archiviare. Si tratta di `NULL` se il controllo del codice sorgente del plug-in una richiesta per un commento.  
  
 fOptions  
 [in] Flag di comando, i valori validi sono 0 o `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|I file è stato correttamente archiviato.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. File non è stato archiviato.|  
|SCC_E_NOTCHECKEDOUT|L'utente non è estratto il file, in modo che non è possibile eseguirne l'archiviazione.|  
|SCC_E_CHECKINCONFLICT|Check-in non può essere eseguita perché:<br /><br /> -Un altro utente è stata archiviata direttamente e `bAutoReconcile` fosse falsa.<br /><br /> -oppure-<br /><br /> -Il merge automatico non può essere eseguito (ad esempio, quando i file sono: binari).|  
|SCC_E_VERIFYMERGE|File è stata unita automatico ma non è stato archiviato attesa di verifica dell'utente.|  
|SCC_E_FIXMERGE|File è stata unita automatico ma non è stato archiviato a causa di un conflitto di merge che deve essere risolti manualmente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
|SCC_E_FILENOTEXIST|File locale non è stato trovato.|  
  
## <a name="remarks"></a>Note  
 Il commento viene applicata a tutti i file da archiviare. L'argomento commento può essere un `null` stringa, nel qual caso il plug-in del controllo del codice sorgente può richiedere all'utente una stringa di commento per ogni file.  
  
 Il `fOptions` argomento può essere assegnato il valore di `SCC_KEEP_CHECKEDOUT` flag che indica l'intenzione dell'utente per archiviare il file ed estrarlo di nuovo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
