---
title: Funzione SccProperties | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 020d30c9c81a188e3104928a52e58d7319523338
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914205"
---
# <a name="sccproperties-function"></a>Funzione SccProperties
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa funzione consente di visualizzare proprietà di controllo di origine per un file o progetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
|Valore|Descrizione|  
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
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)

