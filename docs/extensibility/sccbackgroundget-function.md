---
title: SccBackgroundGet (funzione) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701235"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet (funzione)
Questa funzione recupera dal controllo del codice sorgente ognuno dei file specificati senza alcuna interazione da parte dell'utente.

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

[in] Puntatore di contesto del plug-in del controllo del codice sorgente.

 nFile

[in] Numero di file `lpFileNames` specificati nella matrice.

 LpNomidi File

[in, out] Matrice di nomi di file da recuperare.

> [!NOTE]
> I nomi devono essere nomi di file locali completi.

 dwFlags

[in] Flag di`SCC_GET_ALL` `SCC_GET_RECURSIVE`comando ( , ).

 dwBackgroundOperationID

[in] Valore univoco associato a questa operazione.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Operazione completata correttamente.|
|SCC_E_BACKGROUNDGETINPROGRESS|Un recupero in background è già in corso (il plug-in del controllo del codice sorgente deve restituire questo solo se non supporta le operazioni batch simultanee).|
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|

## <a name="remarks"></a>Osservazioni
 Questa funzione viene sempre chiamata su un thread diverso da quello che ha caricato il plug-in del controllo del codice sorgente. Questa funzione non deve restituire fino a quando non viene eseguita; tuttavia, può essere chiamato più volte con più elenchi di file, tutti contemporaneamente.

 L'utilizzo `dwFlags` dell'argomento è lo stesso di [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
