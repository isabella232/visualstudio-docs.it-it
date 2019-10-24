---
title: Funzione SccRename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b2928653507b670160c72ca3ce09a0227a4170
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720759"
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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpFileName

in Nome completo del file che viene rinominato.

 lpNewName

in Nuovo nome completo. Se il percorso della directory è diverso, il file è stato spostato da una sottodirectory a un'altra.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione di ridenominazione completata correttamente.|
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a completare questa operazione.|
|SCC_E_COULDNOTCREATEPROJECT|Non è stato possibile creare il progetto come parte del processo di ridenominazione.|
|SCC_E_OPNOTPERFORMED|L'operazione non è stata eseguita.|
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|

## <a name="remarks"></a>Note
 Questa funzione può essere usata per rinominare un file o spostarla da una posizione a un'altra nel sistema di controllo del codice sorgente. Il plug-in del controllo del codice sorgente non deve tentare di accedere al file su disco. È responsabilità dell'IDE rinominare il file locale.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)