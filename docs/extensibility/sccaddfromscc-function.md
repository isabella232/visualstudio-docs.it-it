---
title: Funzione SccAddFromScc . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701244"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc (funzione)
Questa funzione consente all'utente di cercare i file che sono già nel sistema di controllo del codice sorgente e successivamente rendere tali file parte del progetto corrente. Ad esempio, questa funzione può ottenere un file di intestazione comune nel progetto corrente senza copiare il file. La matrice restituita `lplpFileNames`di file, , contiene l'elenco dei file che l'utente desidera aggiungere al progetto IDE.

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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 lpnFile

[in, out] Buffer per il numero di file che vengono aggiunti. (Questo `NULL` è se la `lplpFileNames` memoria a cui punta sta per essere rilasciata. Vedere Osservazioni per i dettagli.)

 LplpFileNames (Nomifiledidi

[in, out] Matrice di puntatori a tutti i nomi di file senza percorsi di directory. Questa matrice viene allocata e liberata dal plug-in del controllo del codice sorgente. Se `lpnFiles` il `lplpFileNames` valore `NULL`è 1 e non è `lplpFileNames` , il nome dell'array a cui fa riferimento contiene la cartella di destinazione.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|I file sono stati individuati con successo e aggiunti al progetto.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata senza alcun effetto.|
|SCC_I_RELOADFILE|Un file o un progetto deve essere ricaricato.|

## <a name="remarks"></a>Osservazioni
 L'IDE chiama questa funzione. Se il plug-in del controllo del codice sorgente supporta `lpnFiles` la specifica di una cartella `lplpFileNames`di destinazione locale, l'IDE passa il valore 1 e passa il nome della cartella locale in .

 Quando la chiamata `SccAddFromScc` alla funzione restituisce , il `lpnFiles` `lplpFileNames`plug-in ha assegnato valori a e , allocando la `lplpFileNames`memoria per la matrice di nomi di file in base alle esigenze (si noti che questa allocazione sostituisce il puntatore in ). Il plug-in del controllo del codice sorgente è responsabile dell'inserimento di tutti i file nella directory dell'utente o nella cartella di designazione specificata. L'IDE aggiunge quindi i file al progetto IDE.

 Infine, l'IDE chiama questa funzione `NULL` una `lpnFiles`seconda volta, passando per . Questo viene interpretato come un segnale speciale dal plug-in del controllo del codice sorgente per rilasciare la memoria allocata per la matrice di nomi di file in`lplpFileNames``.`

 `lplpFileNames`è `char ***` un puntatore. Il plug-in del controllo del codice sorgente inserisce un puntatore a una matrice di puntatori ai nomi di file, passando così l'elenco nel modo standard per questa API.

> [!NOTE]
> Le versioni iniziali dell'API VSSCI non hanno fornito un modo per indicare il progetto di destinazione per i file aggiunti. Per risolvere questo problema, `lplpFIleNames` la semantica del parametro è stata migliorata per renderlo un parametro in/out anziché un parametro di output. Se viene specificato un solo file, ovvero il `lpnFiles` valore a cui punta `lplpFileNames` il valore è 1, il primo elemento di contiene la cartella di destinazione. Per utilizzare questa nuova semantica, `SccSetOption` l'IDE chiama la funzione con il `nOption`parametro impostato su `SCC_OPT_SHARESUBPROJ`. Se un plug-in del controllo del codice `SCC_E_OPTNOTSUPPORTED`sorgente non supporta la semantica, restituisce . In questo modo viene disabilitato l'utilizzo della funzionalità **Aggiungi dal controllo del codice sorgente.** Se un plug-in supporta la funzionalità **Aggiungi dal controllo del codice sorgente** ( ),`SCC_CAP_ADDFROMSCC`deve supportare la nuova semantica e restituire `SCC_I_SHARESUBPROJOK`.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
