---
description: Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione, ma non per la modifica.
title: Funzione SccGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 805c19b0c326e8389b4e1905edf370ad042aac92
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904552"
---
# <a name="sccget-function"></a>Funzione SccGet
Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione, ma non per la modifica. Nella maggior parte dei sistemi i file sono contrassegnati come di sola lettura.

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

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFile

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi completi di file da recuperare.

 fOpzioni

[in] Flag di comando ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo dell'operazione get.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_FILEISCHECKEDOUT|Impossibile ottenere il file attualmente estratto dall'utente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NOSPECIFIEDVERSION|È stata specificata una versione o una data/ora non valida.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. il file non è stato sincronizzato.|
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|
|SCC_E_NOTAUTHORIZED|Non è disponibile l'autorizzazione per eseguire questa operazione.|

## <a name="remarks"></a>Commenti
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag , significa che gli elementi in non sono file ma directory e che tutti i file sotto controllo del codice sorgente nelle `SCC_GET_ALL` directory specificate devono essere `lpFileNames` recuperati.

 Il flag può essere combinato con il flag per recuperare tutti i file nelle directory specificate e in tutte le `SCC_GET_ALL` `SCC_GET_RECURSIVE` sottodirectory.

> [!NOTE]
> `SCC_GET_RECURSIVE` non deve mai essere passato senza `SCC_GET_ALL` . Si noti inoltre che se le directory *C:\A* e *C:\A\B* vengono entrambe passate a un get ricorsivo, *C:\A\B* e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non del plug-in del controllo del codice sorgente, assicurarsi che i duplicati come questo siano mantenuti fuori dalla matrice.

 Infine, anche se un plug-in del controllo del codice sorgente ha specificato il flag all'inizializzazione, a indicare che non dispone di un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i `SCC_CAP_GET_NOUI` file. Il flag indica semplicemente che l'IDE non visualizza una voce di menu Get e che il plug-in non deve fornire alcuna interfaccia utente.

## <a name="rename-files-and-sccget"></a>Rinominare file e SccGet
 Situazione: un utente esemplifica un file, ad esempio *a.txt* e lo modifica. Prima *chea.txt* possa essere archiviato, un secondo utente rinomina *a.txt* *inb.txt* nel database del controllo del codice sorgente, estrazione *b.txt*, apporta alcune modifiche al file e controlla il file. Il primo utente vuole che le modifiche apportate dal secondo utente in modo che  il primo utente rinomina la versione locale del file *dia.txt* b.txted esegue un'operazione get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione pensa ancora che la prima versione di *a.txt* sia archiviata in locale e quindi il controllo del codice sorgente non possa risolvere le differenze.

 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni del controllo del codice sorgente non è sincronizzata con il database del controllo del codice sorgente:

1. Non consentire la ridenominazione di un file nel database del controllo del codice sorgente attualmente estratto.

2. Eseguire l'equivalente di "delete old" seguito da "add new". L'algoritmo seguente è un modo per eseguire questa operazione.

    1. Chiamare la [funzione SccQueryChanges](../extensibility/sccquerychanges-function.md) per informazioni sulla ridenominazione dia.txt *per* b.txt *nel* database del controllo del codice sorgente.

    2. Rinominare *l'a.txt* locale *inb.txt*.

    3. Chiamare la `SccGet` funzione  sia pera.txtche *perb.txt*.

    4. Poiché *a.txt* non esiste nel database del controllo del codice sorgente,  la cache della versione locale viene eliminata delle informazioni sulla versionea.txtmancanti.

    5. Il *b.txt* file estratto viene unito al contenuto del fileb.txt *locale.*

    6. Il file *b.txt* file può ora essere archiviato.

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
