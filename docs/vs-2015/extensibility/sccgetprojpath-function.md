---
title: Funzione SccGetProjPath | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0809ab976712d45f1cae8ec39990438e591744f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518951"
---
# <a name="sccgetprojpath-function"></a>Funzione SccGetProjPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccGetProjPath](https://docs.microsoft.com/visualstudio/extensibility/sccgetprojpath-function).  
  
Questa funzione richiede all'utente un percorso di progetto, che è una stringa che è significativa solo per il plug-in del controllo del codice sorgente. Viene chiamato quando l'utente è:  
  
-   Crea un nuovo progetto  
  
-   Aggiunta di un progetto esistente al controllo della versione  
  
-   Tentativo di trovare un progetto di controllo di versione esistente  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (senza superare SCC_USER_SIZE, incluso il carattere di terminazione NULL)  
  
 lpProjName  
 [in, out] Il nome del progetto dell'IDE, dell'area di lavoro di progetto o makefile (senza superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 lpLocalPath  
 [in, out] Percorso di lavoro del progetto. Se `bAllowChangePath` è `TRUE`, il plug-in del controllo del codice sorgente è possibile modificare questa stringa (senza superare MAX_PATH, incluso il carattere di terminazione null).  
  
 lpAuxProjPath  
 [in, out] Un buffer per il percorso del progetto restituiti (che non devono superare SCC_PRJPATH_SIZE, incluso il carattere di terminazione NULL).  
  
 bAllowChangePath  
 [in] Se si tratta `TRUE`, il plug-in del controllo del codice sorgente è possibile richiedere e modificare il `lpLocalPath` stringa.  
  
 pbNew  
 [in, out] Valore in arrivo nel indica se creare un nuovo progetto. Valore restituito indica l'esito positivo della creazione di un progetto:  
  
|In ingresso|Interpretazione|  
|--------------|--------------------|  
|true|L'utente può creare un nuovo progetto.|  
|false|L'utente non è stato possibile creare un nuovo progetto.|  
  
|In uscita|Interpretazione|  
|--------------|--------------------|  
|true|È stato creato un nuovo progetto.|  
|false|È stato selezionato un progetto esistente.|  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Il progetto è stata correttamente creato o recuperato.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_CONNECTIONFAILURE|Si è verificato un errore durante il tentativo di connettersi al sistema di controllo di origine.|  
|SCC_E_NONSPECIFICERROR|Si è verificato un errore non specificato.|  
  
## <a name="remarks"></a>Note  
 Lo scopo di questa funzione è per l'IDE acquisire i parametri `lpProjName` e `lpAuxProjPath`. Dopo che il plug-in del controllo del codice sorgente chiede all'utente queste informazioni, tornare all'IDE passa questi due stringhe. L'IDE persiste queste stringhe nel file di soluzione e li passa per la [SccOpenProject](../extensibility/sccopenproject-function.md) ogni volta che l'utente apre questo progetto. Queste stringhe di abilitare il plug-in tenere traccia delle informazioni associate a un progetto.  
  
 Quando la funzione viene chiamata prima di tutto, `lpAuxProjPath` è impostato su una stringa vuota. `lProjName` può anche essere vuoto, o può contenere il nome del progetto IDE, che può usare o ignorare il plug-in del controllo del codice sorgente. Quando la funzione termina correttamente, il plug-in restituisce le due stringhe corrispondenti. L'IDE non fa alcuna ipotesi su queste stringhe, non verrà utilizzati e non consentirà all'utente di modificarli. Se l'utente desidera modificare le impostazioni, l'IDE chiamerà `SccGetProjPath` anche in questo caso, passando gli stessi valori aveva ricevuto l'ora precedente. In questo modo il plug-in del controllo completo su queste due stringhe.  
  
 Per `lpUser`, l'IDE può passare un nome utente o potrebbe semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug-in del controllo del codice sorgente deve usarlo come valore predefinito. Tuttavia, se è stato passato alcun nome o l'account di accesso non riuscito con il nome specificato, il plug-in deve richiedere all'utente per un account di accesso e passare di nuovo il nome `lpUser` quando riceve un account di accesso valido. Poiché il plug-in possono modificare questa stringa, l'IDE sempre dovrà allocare un buffer di dimensione (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  La prima azione che esegue l'IDE può essere una chiamata a uno il `SccOpenProject` funzione o `SccGetProjPath` (funzione). Di conseguenza, entrambe riportano un identico `lpUser` parametro, che consente il plug-in per l'accesso l'utente in fase di controllo del codice sorgente. Anche se il valore restituito dalla funzione indica un errore, il plug-in deve riempire questa stringa con un nome di account di accesso valido.  
  
 `lpLocalPath` è la directory in cui l'utente posiziona il progetto. Potrebbe trattarsi di una stringa vuota. Se è presente alcuna directory attualmente definiti (come nel caso di un utente tenta di scaricare un progetto dal sistema di controllo di origine) e se `bAllowChangePath` è `TRUE`, possa richiedere all'utente per l'input o utilizzare un altro metodo per inserire il plug-in del controllo del codice sorgente relativo proprietà stringa in `lpLocalPath`. Se `bAllowChangePath` è `FALSE`, il plug-in necessario non modificare la stringa, perché l'utente sta già lavorando nella directory specificata.  
  
 Se l'utente crea un nuovo progetto da inserire nel controllo del codice sorgente, il plug-in del controllo del codice sorgente potrebbe non effettivamente crearlo nel sistema di controllo di origine al momento `SccGetProjPath` viene chiamato. Al contrario, passa indietro della stringa con un valore diverso da zero per `pbNew`, che indica che il progetto verrà creato nel sistema di controllo di origine.  
  
 Ad esempio, se un utente del **nuovo progetto** guidata in Visual Studio aggiunge il proprio progetto al controllo del codice sorgente, Visual Studio chiama questa funzione e il plug-in determina se è corretto creare un nuovo progetto nel sistema di controllo di origine a contiene il progetto di Visual Studio. Se l'utente sceglie **annullare** mai creato prima di completare la procedura guidata, il progetto. Se l'utente sceglie **OK**, Visual Studio chiama `SccOpenProject`passando `SCC_OPT_CREATEIFNEW`, e viene creato il progetto di controllo del codice sorgente in quel momento.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

