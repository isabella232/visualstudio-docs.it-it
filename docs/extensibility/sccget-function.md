---
title: Funzione SccGet . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700896"
---
# <a name="sccget-function"></a>SccGet (funzione)
Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione, ma non per la modifica. Nella maggior parte dei sistemi, i file sono contrassegnati come di sola lettura.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 nFile

[in] Numero di file `lpFileNames` specificati nella matrice.

 LpNomidi File

[in] Matrice di nomi completi dei file da recuperare.

 fOpzioni

[in] Flag di`SCC_GET_ALL` `SCC_GET_RECURSIVE`comando ( , ).

 PvOpzioni

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Successo dell'otazione.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_FILEISCHECKEDOUT|Impossibile ottenere il file che l'utente ha attualmente estratto.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NOSPECIFIEDVERSION|Specificata una versione o una data/ora non valida.|
|SCC_E_NONSPECIFICERROR|Errore non specifico; file non è stato sincronizzato.|
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|
|SCC_E_NOTAUTHORIZED|Non è disponibile l'autorizzazione per eseguire questa operazione.|

## <a name="remarks"></a>Osservazioni
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE `SCC_GET_ALL`passa il flag , `lpFileNames` significa che gli elementi in non sono file ma directory e che tutti i file inclusi nel controllo del codice sorgente nelle directory specificate devono essere recuperati.

 Il `SCC_GET_ALL` flag può essere `SCC_GET_RECURSIVE` combinato con il flag per recuperare tutti i file nelle directory specificate e in tutte le sottodirectory.

> [!NOTE]
> `SCC_GET_RECURSIVE`non dovrebbe mai `SCC_GET_ALL`essere passato senza . Si noti inoltre che se le directory *C:* , A e *C:* , A , B vengono entrambe passate su un get ricorsivo, *C: , A , B* e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non del plug-in del controllo del codice sorgente, assicurarsi che i duplicati di questo tipo vengono mantenuti all'esterno della matrice.

 Infine, anche se un plug-in `SCC_CAP_GET_NOUI` del controllo del codice sorgente specificato il flag durante l'inizializzazione, che indica che non dispone di un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i file. Il flag indica semplicemente che l'IDE non visualizza una voce di menu Get e che il plug-in non deve fornire alcuna interfaccia utente.

## <a name="rename-files-and-sccget"></a>Rinominare file e SccGet
 Situazione: un utente estrae un file, ad esempio *a.txt*, e lo modifica. Prima che *a.txt* possa essere archiviato, un secondo utente rinomina *a.txt* in *b.txt* nel database del controllo del codice sorgente, estrae *b.txt*, apporta alcune modifiche al file e archivia il file. Il primo utente desidera le modifiche apportate dal secondo utente in modo che il primo utente rinomina la versione locale del file *a.txt* in *b.txt* e non ottiene il file. Tuttavia, la cache locale che tiene traccia dei numeri di versione pensa ancora che la prima versione di *a.txt* sia archiviata localmente e pertanto il controllo del codice sorgente non è in grado di risolvere le differenze.

 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni del controllo del codice sorgente diventa non sincronizzata con il database del controllo del codice sorgente:There are two ways to resolve this situation where the local cache of source control versions becomes out of sync with the source control database:

1. Non consentire la ridenominazione di un file nel database del controllo del codice sorgente attualmente estratto.

2. Fare l'equivalente di "delete old" seguito da "add new". L'algoritmo seguente è un modo per eseguire questa operazione.

    1. Chiamare la funzione [SccQueryChanges](../extensibility/sccquerychanges-function.md) per informazioni sulla ridenominazione di *a.txt* in *b.txt* nel database del controllo del codice sorgente.

    2. Rinominare il file *a.txt* locale in *b.txt*.

    3. Chiamare `SccGet` la funzione per *a.txt* e *b.txt*.

    4. Poiché *a.txt* non esiste nel database del controllo del codice sorgente, la cache della versione locale viene eliminata dalle informazioni sulla versione *a.txt* mancanti.

    5. Il file *b.txt* in fase di estrazione viene unito al contenuto del file *b.txt* locale.

    6. Il file *b.txt* aggiornato può ora essere archiviato.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit utilizzati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
