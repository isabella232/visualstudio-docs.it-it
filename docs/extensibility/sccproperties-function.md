---
title: Funzione SccProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c8037b69b537a5db3a8e547e5122032097b75fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353555"
---
# <a name="sccproperties-function"></a>Funzione SccProperties
Questa funzione consente di visualizzare proprietà di controllo di origine per un file o progetto.

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

[in] La struttura del contesto plug-in del controllo origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 lpFileName

[in] Il nome e percorso completo del file o progetto.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Le proprietà sono state visualizzate correttamente.|
|SCC_I_RELOADFILE|Il sistema di controllo della versione ha modificato le proprietà del file, in modo che l'IDE deve ricaricare questo file.|
|SCC_E_PROJNOTOPEN|Il progetto specificato non è stata aperta nel controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a visualizzare le proprietà di questo file o progetto.|
|SCC_E_FILENOTCONTROLLED|Il file specificato o il progetto non è sotto controllo del codice sorgente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Si è verificato un errore sconosciuto o generale.|

## <a name="remarks"></a>Note
 Il plug-in del controllo del codice sorgente consente di visualizzare le proprietà in una finestra di dialogo.

 Le proprietà sono definite per il plug-in del controllo del codice sorgente e possono differire dal plug-in a plug-in. Se il plug-in consente all'utente di modificare le proprietà di controllo di origine di un file, deve restituire `SCC_I_RELOAD` per segnalare l'IDE in cui è necessario ricaricare il file o progetto.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)