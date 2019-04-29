---
title: Funzione SccRename | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e270d1be9cdf935dbffa7d094fddaecd4f73a02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433071"
---
# <a name="sccrename-function"></a>Funzione SccRename
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione consente di rinominare un file nel sistema di controllo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 lpFileName  
 [in] Il nome completo del file del file che viene rinominato.  
  
 lpNewName  
 [in] Specificare il nuovo nome completo. Se il percorso della directory è diverso, quindi il file è stato spostato da una sottodirectory a un altro.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|L'operazione di ridenominazione completata correttamente.|  
|SCC_E_PROJNOTOPEN|Il progetto non è aperto nel controllo del codice sorgente.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a completare l'operazione.|  
|SCC_E_COULDNOTCREATEPROJECT|Il progetto non può essere creato come parte del processo di ridenominazione.|  
|SCC_E_OPNOTPERFORMED|Non è stata eseguita l'operazione.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|  
  
## <a name="remarks"></a>Note  
 Questa funzione può essere utilizzata per rinominare un file o viene spostato da una posizione a altra nel sistema di controllo di origine. Il plug-in del controllo del codice sorgente non tentare di accedere al file su disco. È responsabilità dell'IDE per rinominare il file locale.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
