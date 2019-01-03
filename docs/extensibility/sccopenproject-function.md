---
title: Funzione SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fde4a8e59fb64e12b78eacc14406fdf5020b64f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856475"
---
# <a name="sccopenproject-function"></a>Funzione SccOpenProject
Questa funzione consente di aprire un progetto di controllo di origine esistente o ne crea uno nuovo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome dell'utente (senza superare SCC_USER_SIZE, incluso il carattere di terminazione NULL).  
  
 lpProjName  
 [in] Stringa che identifica il nome del progetto.  
  
 lpLocalProjPath  
 [in] Il percorso della cartella di lavoro per il progetto.  
  
 lpAuxProjPath  
 [in, out] Stringa facoltativa ausiliaria che identifica il progetto (non superare SCC_AUXPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpComment  
 [in] Commento a un nuovo progetto in fase di creazione.  
  
 lpTextOutProc  
 [in] Una funzione di callback facoltativo da visualizzare il testo dal controllo del codice sorgente del plug-in di output.  
  
 dwFlags  
 [in] Segnala se deve essere creato se il progetto è sconosciuto all'origine di un nuovo progetto di controllo del plug-in. Valore può essere una combinazione di `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Esito positivo nell'apertura del progetto.|  
|SCC_E_INITIALIZEFAILED|Progetto non è stato possibile inizializzare.|  
|SCC_E_INVALIDUSER|L'utente non può accedere al sistema di controllo di origine.|  
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non esisteva prima della chiamata;  il `SCC_OPT_CREATEIFNEW` flag è stato impostato, ma non è stato possibile creare il progetto.|  
|SCC_E_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC_E_UNKNOWNPROJECT|Il progetto è sconosciuto per il controllo del codice sorgente del plug-in e il `SCC_OPT_CREATEIFNEW` flag non è stato impostato.|  
|SCC_E_INVALIDFILEPATH|Percorso del file non valido o inutilizzabile.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECFICERROR|Un errore non specifico. il controllo del codice sorgente non è stato inizializzato.|  
  
## <a name="remarks"></a>Note  
 L'IDE può passare un nome utente (`lpUser`), oppure potrebbe semplicemente passare in un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve usarlo come valore predefinito. Tuttavia, se è stato passato alcun nome, o se l'account di accesso non riuscito con il nome specificato, il plug-in deve richiedere all'utente di accedere e verrà restituito il nome valido in `lpUser` quando riceve un account di accesso valido`.` perché il plug-in può cambiare la stringa del nome utente , l'IDE sempre dovrà allocare un buffer di dimensione (`SCC_USER_LEN`SCC_USER_SIZE, che include lo spazio per il carattere null di terminazione o + 1).  
  
> [!NOTE]
>  La prima azione dell'IDE potrebbe essere necessario eseguire può essere una chiamata ai `SccOpenProject` funzione o il [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Per questo motivo, li dispongono di un'identica `lpUser` parametro.  
  
 `lpAuxProjPath` e`lpProjName` vengono lette dal file di soluzione, o vengono restituiti da una chiamata al `SccGetProjPath` (funzione). Questi parametri contengano le stringhe che associa il controllo del codice sorgente del plug-in al progetto e sono significativi solo per il plug-in. Se ad esempio stringhe non sono nel file di soluzione e l'utente non è stato richiesto di passare (che restituirà una stringa tramite il `SccGetProjPath` (funzione)), l'IDE passa stringhe vuote per entrambe `lpAuxProjPath` e `lpProjName`e si aspetta che questi valori da aggiornare per il plug-in del momento in cui questa funzione restituisce.  
  
 `lpTextOutProc` è un puntatore a una funzione di callback fornita dall'IDE per il controllo del codice sorgente del plug-in per la visualizzazione dell'output di risultato del comando. Questa funzione di callback è descritto dettagliatamente [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Se il plug-in del controllo del codice sorgente è intenzione di sfruttare i vantaggi di questo, è necessario impostare il `SCC_CAP_TEXTOUT` flag nel [SccInitialize](../extensibility/sccinitialize-function.md). Se questo flag non è stata impostata o se l'IDE non supporta questa funzionalità `lpTextOutProc` saranno `NULL`.  
  
 Il `dwFlags` parametro controlla il risultato nel caso in cui il progetto in fase di apertura non esiste attualmente. È costituito da due flag di bit, `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN`. Se il progetto in corso l'apertura già esiste, la funzione semplicemente il progetto verrà aperto e restituisce `SCC_OK`. Se il progetto non esiste e se il `SCC_OP_CREATEIFNEW` flag è attivato, il plug-in del controllo del codice sorgente può creare il progetto nel sistema di controllo di origine, aprirlo e restituire `SCC_OK`. Se il progetto non esiste e se il `SCC_OP_CREATEIFNEW` flag è disattivata, il plug-in deve quindi cercare il `SCC_OP_SILENTOPEN` flag. Se tale flag è disattivata, il plug-in possono richiedere all'utente per un nome di progetto. Se tale flag è attivato, il plug-in deve semplicemente restituire `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Ordine di chiamata  
 Durante il normale funzionamento degli eventi, il [SccInitialize](../extensibility/sccinitialize-function.md) deve essere chiamato prima di tutto per aprire una sessione di controllo di origine. Una sessione può essere costituita da una chiamata a `SccOpenProject`, seguita da altre chiamate di funzioni API dei plug-in del controllo sorgente e terminerà con una chiamata ai [SccCloseProject](../extensibility/scccloseproject-function.md). Tali sessioni possono essere ripetuti più volte prima la [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.  
  
 Se l'origine di controllo set di plug-in di `SCC_CAP_REENTRANT` di tipo bit in `SccInitialize`, quindi la sequenza di sessione precedente può essere ripetuta più volte in parallelo. Diversi `pvContext` strutture di tenere traccia delle sessioni diverse, in cui ogni `pvContext` è associato a un progetto aperto in una fase. Base di`pvContext` parametro, il plug-in grado di determinare quale progetto si fa riferimento in qualsiasi particolare chiamata. Se la funzionalità di tipo bit `SCC_CAP_REENTRANT` non è impostata, nonreentrant plug-in controllo codice sorgente sono limitate le possibilità di lavorare con più progetti.  
  
> [!NOTE]
>  Il `SCC_CAP_REENTRANT` bit è stato introdotto nella versione 1.1 dell'API dei plug-in controllo di origine. Non è impostata oppure viene ignorato nella versione 1.0 e tutti versione 1.0 origine plug-in del controllo si presuppone che siano nonreentrant.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Limitazioni sulle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)