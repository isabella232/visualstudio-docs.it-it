---
title: Funzione SccRemove | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70413c2e446f8ed226a58eb8ddfe62ede4a1d61f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338627"
---
# <a name="sccremove-function"></a>Funzione SccRemove
Questa funzione Elimina i file dal sistema di controllo di origine.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
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

[in] Numero di file specificato per il `lpFileNames` matrice.

 lpFileNames

[in] Matrice di nomi di percorso locale completo dei file da rimuovere.

 lpComment

[in] Il commento da applicare a ogni file rimosso.

 fOptions

[in] Flag di comando (non usato).

 pvOptions

[in] Opzioni specifiche plug-in controllo sorgente.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|La rimozione è stata completata.|
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ISCHECKEDOUT|Impossibile rimuovere un file perché un utente è attualmente estratto.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. file non è stato rimosso.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Note
 Questa funzione rimuove i file dal sistema di controllo di origine ma non li elimina dal disco rigido locale dell'utente.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)