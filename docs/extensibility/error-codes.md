---
title: Codici di errore | Microsoft Docs
description: Questo articolo contiene un elenco di codici di errore, valori e descrizioni per le funzioni api plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eedc9311bcafdd4241e065b40079abed3977dcef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898305"
---
# <a name="error-codes"></a>Codici di errore
Quando una funzione API plug-in del controllo del codice sorgente restituisce un errore, è previsto che sia uno dei codici di errore seguenti. Tutti gli errori sono negativi, gli avvisi o i codici di errore in informazioni sono positivi e l'esito positivo è 0.

|Codice di errore|Valore|Descrizione|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Il plug-in supporta l'aggiunta di file dal controllo del codice sorgente in due passaggi. Per altre informazioni, vedere [SccSetOption.](../extensibility/sccsetoption-function.md)|
|`SCC_I_FILEDIFFERS`|6|Il file locale è diverso dal file nel database del controllo del codice sorgente (ad esempio, [SccDiff](../extensibility/sccdiff-function.md) può restituire questo valore).|
|`SCC_I_RELOADFILE`|5|Il file locale è stato modificato durante l'operazione di controllo del codice sorgente. L'IDE deve ricaricare il file, se possibile.|
|`SCC_I_FILENOTAFFECTED`|4|Il file non è interessato.|
|`SCC_I_PROJECTCREATED`|3|Il progetto è stato creato durante l'operazione di controllo del codice sorgente, ad esempio durante una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md) quando `SCC_OP_CREATEIFNEW` è specificato il flag .|
|`SCC_I_OPERATIONCANCELED`|2|Operazione annullata.|
|`SCC_I_ADV_SUPPORT`|1|Il plug-in supporta le opzioni avanzate per il comando specificato. Per altre informazioni, vedere [SccGetCommandOptions.](../extensibility/sccgetcommandoptions-function.md)|
|`SCC_OK`|0|Esito positivo.|
|`SCC_E_INITIALIZEFAILED`|-1|Errore: inizializzazione non riuscita.|
|`SCC_E_UNKNOWNPROJECT`|-2|Errore: progetto sconosciuto.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Errore: impossibile creare il progetto.|
|`SCC_E_NOTCHECKEDOUT`|-4|Errore: il file non è estratto.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Errore: il file è già estratto.|
|`SCC_E_FILEISLOCKED`|-6|Errore: il file è bloccato.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Errore: il file è estratto in modo esclusivo.|
|`SCC_E_ACCESSFAILURE`|-8|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|`SCC_E_CHECKINCONFLICT`|-9|Errore: si è verificato un conflitto durante l'archiviazione.|
|`SCC_E_FILEALREADYEXISTS`|-10|Errore: il file esiste già.|
|`SCC_E_FILENOTCONTROLLED`|-11|Errore: il file non è in controllo del codice sorgente.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Errore: il file è stato estratto.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Errore: non esiste una versione specificata.|
|`SCC_E_OPNOTSUPPORTED`|-14|Errore: l'operazione non è supportata.|
|`SCC_E_NONSPECIFICERROR`|-15|Errore non specifico.|
|`SCC_E_OPNOTPERFORMED`|-16|Errore. L'operazione non è stata eseguita.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Errore: il tipo di file, ad esempio binary, non è supportato dal sistema di controllo del codice sorgente.|
|`SCC_E_VERIFYMERGE`|-18|Il file è stato unito automaticamente ma non è stato controllato perché è in attesa di verifica dell'utente.|
|`SCC_E_FIXMERGE`|-19|Il file è stato unito automaticamente ma non è stato archiviato a causa di un conflitto di merge che deve essere risolto manualmente.|
|`SCC_E_SHELLFAILURE`|-20|Errore dovuto a un errore della shell.|
|`SCC_E_INVALIDUSER`|-21|Errore: l'utente non è valido.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Errore: il progetto è già aperto.|
|`SCC_E_PROJSYNTAXERR`|-23|Errore di sintassi del progetto.|
|`SCC_E_INVALIDFILEPATH`|-24|Errore: il percorso del file non è valido.|
|`SCC_E_PROJNOTOPEN`|-25|Errore: il progetto non è aperto.|
|`SCC_E_NOTAUTHORIZED`|-26|Errore: l'utente non è autorizzato a eseguire questa operazione.|
|`SCC_E_FILESYNTAXERR`|-27|Errore di sintassi del file.|
|`SCC_E_FILENOTEXIST`|-28|Errore. Il file locale non esiste.|
|`SCC_E_CONNECTIONFAILURE`|-29|Errore: si è verificato un errore di connessione.|
|`SCC_E_UNKNOWNERROR`|-30|Errore sconosciuto.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|L'operazione get in background è attualmente in corso.|

## <a name="macros-provided-for-quick-checking"></a>Macro fornite per un controllo rapido

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Commenti
 Tutte le funzioni API del plug-in del controllo del codice sorgente (ad eccezione di [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)e [SccDiff](../extensibility/sccdiff-function.md)) hanno esito positivo quando i file locali passati come argomenti non esistono nella cartella di lavoro. Ad esempio, l'IDE può eseguire una chiamata a [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) su un file che non esiste nella cartella di lavoro, ma esiste nel sistema di controllo del codice sorgente. Questa chiamata avrà esito positivo. Solo quando non è presente alcun file nella cartella di lavoro o nel sistema di controllo del codice sorgente, la funzione dovrebbe avere esito negativo.

 Alcune funzioni, ad esempio e , devono restituire in modo `SccAdd` specifico quando il file nella cartella di lavoro non `SccCheckin` `SCC_E_FILENOTEXIST` esiste. È previsto che altre funzioni riescano quando il file di lavoro non esiste, se le funzioni operano su un nome di file valido nel sistema di controllo del codice sorgente.

 Il plug-in del controllo del codice sorgente non deve fare supposizioni relative ai privilegi per un file nella cartella di lavoro, anche se il plug-in ha contrassegnato il file come di sola lettura durante un'operazione. Un file nella cartella di lavoro può essere spostato, eliminato e modificato all'esterno del controllo del plug-in.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
