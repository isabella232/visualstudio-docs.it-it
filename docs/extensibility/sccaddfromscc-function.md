---
description: Questa funzione consente all'utente di cercare i file già presenti nel sistema di controllo del codice sorgente e successivamente di renderli parte del progetto corrente.
title: Funzione SccAddFromScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48560f135d73c4e53ba132845f4c768cdf4ac982
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904877"
---
# <a name="sccaddfromscc-function"></a>Funzione SccAddFromScc
Questa funzione consente all'utente di cercare i file già presenti nel sistema di controllo del codice sorgente e successivamente di renderli parte del progetto corrente. Ad esempio, questa funzione può ottenere un file di intestazione comune nel progetto corrente senza copiare il file. La matrice di file restituita, , contiene l'elenco di file che `lplpFileNames` l'utente vuole aggiungere al progetto IDE.

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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpnFiles

[in, out] Buffer per il numero di file da aggiungere. Questo valore è `NULL` se la memoria a cui punta deve essere `lplpFileNames` rilasciata. Per informazioni dettagliate, vedere La sezione Osservazioni.

 lplpFileNames

[in, out] Matrice di puntatori a tutti i nomi di file senza percorsi di directory. Questa matrice viene allocata e liberata dal plug-in del controllo del codice sorgente. Se = 1 e non è , il nome nella matrice a cui punta `lpnFiles` contiene la cartella di `lplpFileNames` `NULL` `lplpFileNames` destinazione.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|I file sono stati individuati e aggiunti al progetto.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata senza alcun effetto.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione. Se il plug-in del controllo del codice sorgente supporta la specifica di una cartella di destinazione locale, l'IDE passa = 1 e passa il `lpnFiles` nome della cartella locale in `lplpFileNames` .

 Quando la chiamata alla funzione viene restituita, il plug-in ha assegnato valori a e , allocando la memoria per la matrice di nomi file in base alle esigenze (si noti che questa allocazione sostituisce il puntatore `SccAddFromScc` `lpnFiles` in `lplpFileNames` `lplpFileNames` ). Il plug-in del controllo del codice sorgente è responsabile dell'inserimento di tutti i file nella directory dell'utente o nella cartella di designazione specificata. L'IDE aggiunge quindi i file al progetto IDE.

 Infine, l'IDE chiama questa funzione una seconda volta, passando `NULL` per `lpnFiles` . Viene interpretato come un segnale speciale dal plug-in del controllo del codice sorgente per rilasciare la memoria allocata per la matrice di nomi file in `lplpFileNames``.`

 `lplpFileNames` è un `char ***` puntatore . Il plug-in del controllo del codice sorgente inserisce un puntatore a una matrice di puntatori ai nomi di file, passando l'elenco in modo standard per questa API.

> [!NOTE]
> Le versioni iniziali dell'API VSSCI non hanno fornito un modo per indicare il progetto di destinazione per i file aggiunti. A tale scopo, la semantica del parametro è stata migliorata in modo da renderlo un parametro `lplpFIleNames` in/out anziché un parametro di output. Se viene specificato un solo file, ad esempio il valore a cui punta = 1, il primo `lpnFiles` elemento di contiene la cartella di `lplpFileNames` destinazione. Per usare questa nuova semantica, l'IDE chiama `SccSetOption` la funzione con il parametro impostato su `nOption` `SCC_OPT_SHARESUBPROJ` . Se un plug-in del controllo del codice sorgente non supporta la semantica, restituisce `SCC_E_OPTNOTSUPPORTED` . In questo modo si disabilita l'uso della **funzionalità Aggiungi dal controllo del codice sorgente.** Se un plug-in supporta la funzionalità Aggiungi **dal** controllo del codice sorgente ( ), deve `SCC_CAP_ADDFROMSCC` supportare la nuova semantica e restituire `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
