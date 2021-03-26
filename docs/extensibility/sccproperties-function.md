---
description: Questa funzione consente di visualizzare le proprietà del controllo del codice sorgente per un file o un progetto.
title: Funzione SccProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 56306bb7c248ea500e16964c0929f34a27187298
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056519"
---
# <a name="sccproperties-function"></a>Funzione SccProperties
Questa funzione consente di visualizzare le proprietà del controllo del codice sorgente per un file o un progetto.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parametri
 pvContext

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpFileName

in Nome del percorso completo del file o del progetto.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Le proprietà sono state visualizzate correttamente.|
|SCC_I_RELOADFILE|Il sistema di controllo della versione ha modificato le proprietà del file, quindi l'IDE deve ricaricare il file.|
|SCC_E_PROJNOTOPEN|Il progetto specificato non è stato aperto nel controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a visualizzare le proprietà di questo file o progetto.|
|SCC_E_FILENOTCONTROLLED|Il file o il progetto specificato non è sotto il controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Si è verificato un errore sconosciuto o generico.|

## <a name="remarks"></a>Commenti
 Il plug-in del controllo del codice sorgente Visualizza le proprietà nella relativa finestra di dialogo.

 Le proprietà sono definite dal plug-in del controllo del codice sorgente e possono essere diverse dal plug-in per il plug-in. Se il plug-in consente all'utente di modificare le proprietà del controllo del codice sorgente di un file, deve restituire `SCC_I_RELOAD` per segnalare all'IDE che il file o il progetto deve essere ricaricato.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
