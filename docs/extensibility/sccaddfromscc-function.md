---
description: Questa funzione consente all'utente di cercare i file già presenti nel sistema di controllo del codice sorgente e successivamente di fare in modo che tali file facciano parte del progetto corrente.
title: Funzione SccAddFromScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: be67fd18c6cac7217da0d79aaef766e942e15fb9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085676"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc (funzione)
Questa funzione consente all'utente di cercare i file già presenti nel sistema di controllo del codice sorgente e successivamente di fare in modo che tali file facciano parte del progetto corrente. Questa funzione, ad esempio, può ottenere un file di intestazione comune nel progetto corrente senza copiare il file. La matrice di file restituita, `lplpFileNames` , contiene l'elenco di file che l'utente desidera aggiungere al progetto IDE.

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpnFiles

[in, out] Buffer per il numero di file in fase di aggiunta. Ovvero `NULL` se la memoria a cui fa riferimento deve `lplpFileNames` essere rilasciata. Per informazioni dettagliate, vedere la sezione Osservazioni.

 lplpFileNames

[in, out] Matrice di puntatori a tutti i nomi di file senza percorsi di directory. Questa matrice viene allocata e liberata dal plug-in del controllo del codice sorgente. Se `lpnFiles` = 1 e `lplpFileNames` non è `NULL` , il primo nome nella matrice a cui punta `lplpFileNames` contiene la cartella di destinazione.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|I file sono stati individuati e aggiunti al progetto.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata senza alcun effetto.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione. Se il plug-in del controllo del codice sorgente supporta la specifica di una cartella di destinazione locale, l'IDE passa `lpnFiles` = 1 e passa il nome della cartella locale a `lplpFileNames` .

 Quando la chiamata alla `SccAddFromScc` funzione restituisce, il plug-in ha assegnato i valori a `lpnFiles` e `lplpFileNames` , allocando la memoria per la matrice di nomi di file secondo necessità (si noti che questa allocazione sostituisce il puntatore in `lplpFileNames` ). Il plug-in del controllo del codice sorgente è responsabile dell'inserimento di tutti i file nella directory dell'utente o nella cartella designazione specificata. L'IDE aggiunge quindi i file al progetto IDE.

 Infine, l'IDE chiama questa funzione una seconda volta, passando `NULL` per `lpnFiles` . Questo viene interpretato come un segnale speciale dal plug-in del controllo del codice sorgente per rilasciare la memoria allocata per la matrice di nomi di file in `lplpFileNames``.`

 `lplpFileNames` è un `char ***` puntatore. Il plug-in del controllo del codice sorgente inserisce un puntatore a una matrice di puntatori ai nomi di file, passando l'elenco nel modo standard per questa API.

> [!NOTE]
> Le versioni iniziali dell'API VSSCI non forniscono un modo per indicare il progetto di destinazione per i file aggiunti. Per risolvere questo problema, la semantica del `lplpFIleNames` parametro è stata migliorata in modo da renderla un parametro in/out anziché un parametro di output. Se viene specificato un solo file, ovvero il valore a cui punta `lpnFiles` = 1, il primo elemento di `lplpFileNames` contiene la cartella di destinazione. Per usare la nuova semantica, l'IDE chiama la `SccSetOption` funzione con il `nOption` parametro impostato su `SCC_OPT_SHARESUBPROJ` . Se un plug-in del controllo del codice sorgente non supporta la semantica, restituisce `SCC_E_OPTNOTSUPPORTED` . Questa operazione Disabilita l'uso della funzionalità **Aggiungi da controllo del codice sorgente** . Se un plug-in supporta la funzionalità **Aggiungi da controllo del codice sorgente** ( `SCC_CAP_ADDFROMSCC` ), deve supportare la nuova semantica e restituire `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
