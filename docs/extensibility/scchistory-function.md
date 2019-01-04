---
title: Funzione SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adf1cf2c408cf089d559c4c7d8c443470743fbc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956907"
---
# <a name="scchistory-function"></a>Funzione SccHistory
Questa funzione consente di visualizzare la cronologia dei file specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvContext`  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 `hWnd`  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 `nFiles`  
 [in] Numero di file specificato per il `lpFileName` matrice.  
  
 `lpFileName`  
 [in] Matrice di nomi completi di file.  
  
 `fOptions`  
 [in] Flag di comando (attualmente non usato).  
  
 `pvOptions`  
 [in] Opzioni specifiche plug-in controllo sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Cronologia delle versioni è stata ottenuta correttamente.|  
|SCC_I_RELOADFILE|Il controllo del codice sorgente modificato effettivamente il file su disco durante il recupero della cronologia (ad esempio, ottenendo una versione precedente), in modo che l'IDE deve ricaricare questo file.|  
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC_E_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_PROJNOTOPEN|Il progetto non sia stata aperta.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico. Non è stato possibile ottenere la cronologia dei file.|  
  
## <a name="remarks"></a>Note  
 Il plug-in del controllo del codice sorgente può visualizzare una finestra di dialogo per visualizzare la cronologia di ogni file, usando `hWnd` come finestra padre. In alternativa, il testo facoltativo output callback funzione fornito per il [SccOpenProject](../extensibility/sccopenproject-function.md) può essere utilizzato, se è supportata.  
  
 Si noti che in determinate circostanze, il file in corso l'analisi potrebbe cambiare durante l'esecuzione di questa chiamata. Ad esempio, il [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando Cronologia consente all'utente la possibilità di ottenere una versione precedente del file. In tal caso, l'origine di controllo del plug-in restituisce `SCC_I_RELOAD` per avvisare l'IDE ed è necessario ricaricare il file.  
  
> [!NOTE]
>  Se il plug-in del controllo del codice sorgente non supporta questa funzione per una matrice di file, può essere visualizzata solo la cronologia file per il primo file.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)