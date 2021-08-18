---
description: Questa funzione recupera dal controllo del codice sorgente ognuno dei file specificati senza alcuna interazione dell'utente.
title: Funzione SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f010aa2ba214004422048513cea92adf67d62c69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144626"
---
# <a name="sccbackgroundget-function"></a>Funzione SccBackgroundGet
Questa funzione recupera dal controllo del codice sorgente ognuno dei file specificati senza alcuna interazione dell'utente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Puntatore al contesto del plug-in del controllo del codice sorgente.

 nFile

[in] Numero di file specificati nella `lpFileNames` matrice.

 lpFileNames

[in, out] Matrice di nomi di file da recuperare.

> [!NOTE]
> I nomi devono essere nomi di file locali completi.

 dwFlags

[in] Flag di comando ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

[in] Valore univoco associato a questa operazione.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata correttamente.|
|SCC_E_BACKGROUNDGETINPROGRESS|È già in corso un recupero in background. Il plug-in del controllo del codice sorgente deve restituire questo valore solo se non supporta operazioni batch simultanee.|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Commenti
 Questa funzione viene sempre chiamata su un thread diverso da quello che ha caricato il plug-in del controllo del codice sorgente. Questa funzione non deve restituire finché non viene eseguita. tuttavia, può essere chiamato più volte con più elenchi di file, tutti contemporaneamente.

 L'uso `dwFlags` dell'argomento è lo stesso di [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
