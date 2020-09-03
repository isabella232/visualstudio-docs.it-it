---
title: Funzione SccCheckout | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f23290ebfadd1b6e3d34f808d5ea0ccccbb3c319
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200148"
---
# <a name="scccheckout-function"></a>Funzione SccCheckout
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dato un elenco di nomi di file completi, questa funzione li estrae nell'unità locale. Il commento si applica a tutti i file estratti. L'argomento comment può essere una `null` stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccCheckout (  
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
 in Struttura del contesto del plug-in del controllo del codice sorgente.  
  
 hWnd  
 in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.  
  
 nFile  
 in Numero di file selezionati per il controllo.  
  
 lpFileNames  
 in Matrice di nomi di percorsi locali completi dei file da estrarre.  
  
 lpComment  
 in Commento da applicare a ognuno dei file selezionati estratti.  
  
 fOptions  
 in Flag di comando (vedere [flag usato da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 in Opzioni specifiche del plug-in del controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Estrazione riuscita.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è sotto il controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. Il file non è stato estratto.|  
|SCC_E_ALREADYCHECKEDOUT|Il file è già stato estratto dall'utente.|  
|SCC_E_FILEISLOCKED|Il file è bloccato, impedendo la creazione di nuove versioni.|  
|SCC_E_FILEOUTEXCLUSIVE|Un altro utente ha eseguito un'estrazione esclusiva sul file.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)
