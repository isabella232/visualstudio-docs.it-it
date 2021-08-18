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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0c2b3927da5b7d59100a31e9c347d4f32e2118e3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049519"
---
# <a name="sccget-function"></a>Funzione SccGet
Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione, ma non per la modifica. Nella maggior parte dei sistemi, i file vengono contrassegnati come di sola lettura.

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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 nFiles

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi completi dei file da recuperare.

 fOptions

[in] Flag di comando ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Esito positivo dell'operazione get.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_FILEISCHECKEDOUT|Impossibile ottenere il file attualmente estratto dall'utente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_NOSPECIFIEDVERSION|È stata specificata una versione o una data/ora non valida.|
|SCC_E_NONSPECIFICERROR|Errore non specifico; Il file non è stato sincronizzato.|
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|
|SCC_E_NOTAUTHORIZED|Non è disponibile l'autorizzazione per eseguire questa operazione.|

## <a name="remarks"></a>Commenti
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag , significa che gli elementi in non sono file ma directory e che tutti i file in controllo del codice sorgente nelle directory `SCC_GET_ALL` `lpFileNames` specificate devono essere recuperati.

 Il flag può essere combinato con il flag per recuperare tutti i file nelle directory specificate e in `SCC_GET_ALL` `SCC_GET_RECURSIVE` tutte le sottodirectory.

> [!NOTE]
> `SCC_GET_RECURSIVE` non deve mai essere passato senza `SCC_GET_ALL` . Si noti anche che se le directory *C:\A* e *C:\A\B* vengono entrambe passate a un get ricorsivo, *C:\A\B* e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non del plug-in del controllo del codice sorgente, assicurarsi che i duplicati come questo siano mantenuti fuori dalla matrice.

 Infine, anche se un plug-in del controllo del codice sorgente ha specificato il flag durante l'inizializzazione, a indicare che non dispone di un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i `SCC_CAP_GET_NOUI` file. Il flag indica semplicemente che l'IDE non visualizza una voce di menu Get e che il plug-in non deve fornire alcuna interfaccia utente.

## <a name="rename-files-and-sccget"></a>Rinominare file e SccGet
 Situazione: un utente esemplifica un file, ad *esempio,a.txt* e lo modifica. Prima *a.txt* possibile archiviarea.txt, un secondo utente rinomina *a.txt* in *b.txt* nel database del controllo del codice sorgente, esemina *b.txt*, apporta alcune modifiche al file e lo controlla. Il primo utente vuole le modifiche apportate dal secondo utente in modo che il primo utente rinomina la versione locale del file *a.txt* in *b.txt* ed esegue un'operazione get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione continua a pensare che la prima versione di *a.txt* sia archiviata in locale e pertanto il controllo del codice sorgente non è in grado di risolvere le differenze.

 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni del controllo del codice sorgente non è sincronizzata con il database del controllo del codice sorgente:

1. Non consentire la ridenominazione di un file nel database del controllo del codice sorgente attualmente estratto.

2. Eseguire l'equivalente di "delete old" seguito da "add new". L'algoritmo seguente è un modo per eseguire questa operazione.

    1. Chiamare la [funzione SccQueryChanges](../extensibility/sccquerychanges-function.md) per informazioni sulla ridenominazione dia.txt *per* b.txt *nel* database del controllo del codice sorgente.

    2. Rinominare *l'a.txt* locale *inb.txt*.

    3. Chiamare la `SccGet` funzione sia per *a.txt* che *perb.txt*.

    4. Poiché *a.txt* non esiste nel database del controllo del codice sorgente,  la cache della versione locale viene ripulita delle informazioni sulla versionea.txtmancanti.

    5. Il *b.txt* file da estrazione viene unito al contenuto del file *b.txt* locale.

    6. È ora *b.txt* possibile archiviare il file di dati aggiornato.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
