---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742878"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Legge le proprietà specificate dal set di proprietà corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Parametri
 `cpspec`

in Numero di proprietà specificate nella matrice `rgpspec`. Se è zero, il metodo non restituisce alcuna proprietà ma restituisce `S_OK` come codice di esito positivo.

 `rgpspec`

in Matrice di proprietà da leggere. Le proprietà possono essere specificate da un ID di proprietà o da un nome di stringa facoltativo. Non è necessario specificare le proprietà in un ordine particolare nella matrice. La matrice può contenere proprietà duplicate, con la conseguente restituzione di valori di proprietà duplicati per le proprietà semplici. Le proprietà non semplici dovrebbero restituire accesso negato per un tentativo di aprirle una seconda volta. La matrice può contenere una combinazione di ID di proprietà e ID di stringa. Questa matrice deve contenere almeno `cpspec` numero di valori di proprietà.

 `rgvar`

[in, out] Matrice di strutture di `PROPVARIANT`, nello spazio dei nomi Microsoft. VisualStudio. OLE. Interop, da compilare con i valori per ogni proprietà. La matrice deve contenere almeno `cpspec` elementi di dimensioni. Il chiamante non deve inizializzare i valori nella matrice.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non è stata trovata una o più delle proprietà. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se una proprietà non viene trovata, la voce corrispondente nella matrice di `rgvar` contiene una `VARIANT` con il tipo di `VT_EMPTY`.

## <a name="see-also"></a>Vedere anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)