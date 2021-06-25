---
description: Questa funzione visualizza le proprietà del controllo del codice sorgente per un file o un progetto.
title: Funzione SccProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: cd50353ab29c05e5e5db2dc2b3f363af46ca8aa7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904191"
---
# <a name="sccproperties-function"></a>Funzione SccProperties
Questa funzione visualizza le proprietà del controllo del codice sorgente per un file o un progetto.

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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpFileName

[in] Nome completo del percorso del file o del progetto.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Le proprietà sono state visualizzate correttamente.|
|SCC_I_RELOADFILE|Il sistema di controllo della versione ha modificato le proprietà del file, quindi l'IDE deve ricaricare questo file.|
|SCC_E_PROJNOTOPEN|Il progetto specificato non è stato aperto nel controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a visualizzare le proprietà di questo file o progetto.|
|SCC_E_FILENOTCONTROLLED|Il file o il progetto specificato non è in controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Si è verificato un errore sconosciuto o generale.|

## <a name="remarks"></a>Commenti
 Il plug-in del controllo del codice sorgente visualizza le proprietà nella relativa finestra di dialogo.

 Le proprietà sono definite dal plug-in del controllo del codice sorgente e possono differire da plug-in a plug-in. Se il plug-in consente all'utente di modificare le proprietà del controllo del codice sorgente di un file, deve tornare a segnalare all'IDE che il file o il progetto deve `SCC_I_RELOAD` essere ricaricato.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
