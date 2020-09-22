---
title: Funzione SccGet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a5d5065ca427f0319174aa59e6b87d356816d4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839655"
---
# <a name="sccget-function"></a>Funzione SccGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione, ma non per la modifica. Nella maggior parte dei sistemi, i file vengono contrassegnati come di sola lettura.  
  
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
 in Struttura del contesto del plug-in del controllo del codice sorgente.  
  
 hWnd  
 in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.  
  
 nFile  
 in Numero di file specificati nella `lpFileNames` matrice.  
  
 lpFileNames  
 in Matrice di nomi completi di file da recuperare.  
  
 fOptions  
 in Flag di comando ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).  
  
 pvOptions  
 in Opzioni specifiche del plug-in del controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Operazione di Get completata.|  
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|  
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_FILEISCHECKEDOUT|Non è possibile ottenere il file attualmente estratto dall'utente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|  
|SCC_E_NOSPECIFIEDVERSION|È stata specificata una versione o una data/ora non valida.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. il file non è stato sincronizzato.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC_E_NOTAUTHORIZED|Non è disponibile l'autorizzazione per eseguire questa operazione.|  
  
## <a name="remarks"></a>Commenti  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag `SCC_GET_ALL` , significa che gli elementi in `lpFileNames` non sono file, ma directory e che devono essere recuperati tutti i file nel controllo del codice sorgente nelle directory specificate.  
  
 Il `SCC_GET_ALL` flag può essere combinato con il `SCC_GET_RECURSIVE` flag per recuperare anche tutti i file nelle directory specificate e in tutte le sottodirectory.  
  
> [!NOTE]
> `SCC_GET_RECURSIVE` non deve mai essere passato senza `SCC_GET_ALL` . Si noti inoltre che se le directory C:\A e C:\A\B sono entrambe passate in un oggetto Get ricorsivo, C:\A\B e tutte le relative sottodirectory verranno effettivamente recuperate due volte. Si tratta della responsabilità dell'IDE, non del plug-in del controllo del codice sorgente, per assicurarsi che i duplicati, ad esempio, vengano mantenuti fuori dall'array.  
  
 Infine, anche se un plug-in del controllo del codice sorgente ha specificato il `SCC_CAP_GET_NOUI` flag durante l'inizializzazione, a indicare che non è presente un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i file. Il flag indica semplicemente che l'IDE non visualizza una voce di menu Get e che non è previsto che il plug-in fornisca alcuna interfaccia utente.  
  
## <a name="renaming-and-sccget"></a>Ridenominazione e SccGet  
 Situazione: un utente estrae un file, ad esempio a.txt e lo modifica. Prima che a.txt possa essere archiviato, un secondo utente rinomina a.txt b.txt nel database del controllo del codice sorgente, estrae b.txt, apporta alcune modifiche al file e controlla il file in. Il primo utente desidera le modifiche apportate dal secondo utente, in modo che il primo utente rinomina la versione locale del file a.txt in b.txt ed esegue un'operazione Get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione ritiene ancora che la prima versione di a.txt sia archiviata localmente, quindi il controllo del codice sorgente non può risolvere le differenze.  
  
 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni del controllo del codice sorgente non viene sincronizzata con il database del controllo del codice sorgente:  
  
1. Non consentire la ridenominazione di un file nel database del controllo del codice sorgente attualmente estratto.  
  
2. Eseguire l'equivalente di "Delete Old" seguito da "Add New". L'algoritmo seguente è un modo per eseguire questa operazione.  
  
    1. Chiamare la funzione [SccQueryChanges](../extensibility/sccquerychanges-function.md) per informazioni sulla ridenominazione di a.txt b.txt nel database del controllo del codice sorgente.  
  
    2. Rinominare il a.txt locale con b.txt.  
  
    3. Chiamare la `SccGet` funzione per a.txt e b.txt.  
  
    4. Poiché a.txt non esiste nel database del controllo del codice sorgente, la cache della versione locale viene eliminata dalle informazioni della versione a.txt mancanti.  
  
    5. Il file di b.txt estratto viene unito al contenuto del file di b.txt locale.  
  
    6. È ora possibile archiviare il file di b.txt aggiornato.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
