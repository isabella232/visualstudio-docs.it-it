---
description: Questa funzione rinomina un file nel sistema di controllo del codice sorgente.
title: Funzione SccRename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb3fa392cd4ed31d907fe5913f8d7965a20df05b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900460"
---
# <a name="sccrename-function"></a>Funzione SccRename
Questa funzione rinomina un file nel sistema di controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpFileName

[in] Nome completo del file da rinominare.

 lpNewName

[in] Nuovo nome completo. Se il percorso della directory è diverso, il file è stato spostato da una sottodirectory a un'altra.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|L'operazione di ridenominazione è stata completata.|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a completare questa operazione.|
|SCC_E_COULDNOTCREATEPROJECT|Non è stato possibile creare il progetto come parte del processo di ridenominazione.|
|SCC_E_OPNOTPERFORMED|L'operazione non è stata eseguita.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore generale o non specificato.|

## <a name="remarks"></a>Commenti
 Questa funzione può essere usata per rinominare un file o spostarlo da una posizione a un'altra nel sistema di controllo del codice sorgente. Il plug-in del controllo del codice sorgente non deve tentare di accedere al file su disco. È responsabilità dell'IDE rinominare il file locale.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
