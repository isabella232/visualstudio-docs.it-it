---
title: Funzione SccAddFromScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e02c061e6f85ad25e6cd9509b8a86a977a78cbba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978516"
---
# <a name="sccaddfromscc-function"></a>Funzione SccAddFromScc
Questa funzione consente di individuare i file già presenti nel sistema di controllo di origine e successivamente rendere tali file che fanno parte del progetto corrente. Ad esempio, questa funzione può ottenere un file di intestazione comuni nel progetto corrente senza copiare il file. Alla matrice restituita di file, `lplpFileNames`, contiene l'elenco di file che l'utente desidera aggiungere al progetto IDE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura del contesto plug-in del controllo origine.  
  
 hWnd  
 [in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.  
  
 lpnFiles  
 [in, out] Un buffer per il numero di file che vengono aggiunte in. (Si tratta `NULL` se la memoria a cui punta `lplpFileNames` deve essere rilasciato. Vedere la sezione Osservazioni per informazioni dettagliate).  
  
 lplpFileNames  
 [in, out] Matrice di puntatori a tutti i nomi dei file senza i percorsi di directory. Questa matrice viene allocata e liberata dal plug-in del controllo del codice sorgente. Se `lpnFiles` = 1 e `lplpFileNames` non è `NULL`, il nome della matrice a cui punta `lplpFileNames` contiene la cartella di destinazione.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|SCC_OK|I file sono stati correttamente che si trova e aggiunto al progetto.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata senza alcun effetto.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
  
## <a name="remarks"></a>Note  
 L'IDE chiama questa funzione. Se il controllo del codice sorgente del plug-in supporta la specifica di una cartella di destinazione locale, l'IDE passa `lpnFiles` = 1 e passa il nome di cartella locale in `lplpFileNames`.  
  
 Quando la chiamata ai `SccAddFromScc` funzione termina, il plug-in ha assegnato i valori per `lpnFiles` e `lplpFileNames`, allocazione della memoria per la matrice di nome file in base alle esigenze (si noti che questa allocazione sostituisce il puntatore in `lplpFileNames`). Il plug-in del controllo del codice sorgente è responsabile per l'inserimento di tutti i file nella directory dell'utente o nella cartella designazione specificato. L'IDE aggiunge quindi i file al progetto IDE.  
  
 Infine, l'IDE chiama questa funzione una seconda volta, passando `NULL` per `lpnFiles`. Ciò viene interpretato come un segnale speciale per il plug-in per rilasciare la memoria allocata per la matrice di nomi di file nel controllo del codice sorgente `lplpFileNames``.`  
  
 `lplpFileNames` è un `char ***` puntatore. Il plug-in del controllo del codice sorgente posiziona un puntatore a una matrice di puntatori a nomi di file, quindi passare l'elenco nella modalità standard per questa API.  
  
> [!NOTE]
>  Iniziale versioni dell'API VSSCI non ha fornito un modo per indicare il progetto di destinazione per i file aggiunti. Per supportare questa operazione, la semantica di `lplpFIleNames` parametro sono stati migliorati per renderlo un parametro in/out anziché a un parametro di output. Se solo un singolo file è specificato, vale a dire, il valore a cui punta `lpnFiles` = 1, quindi il primo elemento di `lplpFileNames` contiene la cartella di destinazione. Usare questa nuova semantica, le chiamate IDE di `SccSetOption` utilizzabile con il `nOption`parametro impostato su `SCC_OPT_SHARESUBPROJ`. Se un plug-in del controllo del codice sorgente non supporta la semantica, restituisce `SCC_E_OPTNOTSUPPORTED`. In questo viene disabilitato in questo caso l'utilizzo dei **Aggiungi dal controllo del codice sorgente** funzionalità. Se un plug-in supporta il **Aggiungi dal controllo del codice sorgente** funzionalità (`SCC_CAP_ADDFROMSCC`), quindi deve supportare la nuova semantica e restituire `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)