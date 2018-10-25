---
title: Funzione SccGet | Microsoft Docs
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
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f44b40eae8d67a9efbeed7b2f04b93638db29231
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892646"
---
# <a name="sccget-function"></a>Funzione SccGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione ma non per la modifica. Nella maggior parte dei sistemi, i file vengono contrassegnati come di sola lettura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] Struttura scelta del plug-in del controllo del codice sorgente.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 nFile  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi completi di file da recuperare.  
  
 Opzioni  
 [in] Flag di comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Esito positivo dell'operazione get.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_FILEISCHECKEDOUT|Impossibile ottenere il file che l'utente attualmente è estratto.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NOSPECIFIEDVERSION|Versione non valida o data/ora specificati.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. file non è stata sincronizzata.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
  
## <a name="remarks"></a>Note  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag `SCC_GET_ALL`, questo significa che gli elementi in `lpFileNames` non sono file, ma le directory e che tutti i file in controllo del codice sorgente nella directory specificata devono essere recuperate.  
  
 Il `SCC_GET_ALL` flag può essere combinato con il `SCC_GET_RECURSIVE` flag per recuperare tutti i file nella directory specificata e anche tutte le sottodirectory.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` non deve mai essere passato senza `SCC_GET_ALL`. Si noti inoltre che se le directory C:\A e C:\A\B vengono passati in una ricorsiva get, C:\A\B e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non l'origine di controllo del plug-in, ovvero per assicurarsi che i duplicati di questo vengono mantenuti all'esterno della matrice.  
  
 Infine, anche se i plug-in del controllo del codice sorgente specificato il `SCC_CAP_GET_NOUI` flag durante l'inizializzazione, che indica che non dispone di un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i file. Il flag indica semplicemente che l'IDE non viene visualizzata una voce di menu Get e che il plug-in non è previsto fornire qualsiasi interfaccia utente.  
  
## <a name="renaming-and-sccget"></a>La ridenominazione e SccGet  
 Situazione: un utente estrae un file, ad esempio, txt e lo modifica. Prima di poter essere archiviato txt, un secondo utente rinomina txt in b. txt nel database del controllo del codice sorgente, estrae b. txt, apporta alcune modifiche al file e controlla il file in. Il primo utente desidera le modifiche apportate dall'utente secondo, in modo che il primo utente rinomina la versione locale di un file txt in b. txt ed esegue un'operazione get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione continua a ritenere la prima versione di a. txt viene archiviata in locale e quindi, controllo del codice sorgente non è possibile risolvere le differenze.  
  
 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni di controllo di origine diventa sincronizzata con il database del controllo del codice sorgente:  
  
1.  Non consentire la ridenominazione di un file nel database di controllo di origine che è attualmente estratto.  
  
2.  È l'equivalente di "eliminazione precedente" seguita da "Aggiungi nuovo". L'algoritmo seguente è un modo per eseguire questa operazione.  
  
    1.  Chiamare il [SccQueryChanges](../extensibility/sccquerychanges-function.md) funzione per apprendere la ridenominazione di a. txt in b. txt nel database di controllo di origine.  
  
    2.  Rinominare il txt locale in b. txt.  
  
    3.  Chiamare il `SccGet` funzione txt sia b. txt.  
  
    4.  Poiché txt non esiste nel database del controllo del codice sorgente, le informazioni sulla versione txt mancanti verrà eliminata la cache della versione locale.  
  
    5.  Il file di b. txt in corso l'estrazione viene unito con il contenuto del file locale b. txt.  
  
    6.  Il file aggiornato b. txt può ora essere archiviato.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)

