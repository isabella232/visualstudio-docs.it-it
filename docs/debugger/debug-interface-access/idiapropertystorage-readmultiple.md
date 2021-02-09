---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45eaed0b3306ba0ab1c448d5e61657f0461a9474
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855550"
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

in Numero di proprietà specificate nella `rgpspec` matrice. Se è zero, il metodo non restituisce alcuna proprietà ma restituisce `S_OK` un codice di esito positivo.

 `rgpspec`

in Matrice di proprietà da leggere. Le proprietà possono essere specificate da un ID di proprietà o da un nome di stringa facoltativo. Non è necessario specificare le proprietà in un ordine particolare nella matrice. La matrice può contenere proprietà duplicate, con la conseguente restituzione di valori di proprietà duplicati per le proprietà semplici. Le proprietà non semplici dovrebbero restituire accesso negato per un tentativo di aprirle una seconda volta. La matrice può contenere una combinazione di ID di proprietà e ID di stringa. Questa matrice deve contenere almeno un `cpspec` numero di valori di proprietà.

 `rgvar`

[in, out] Matrice di `PROPVARIANT` strutture (nello spazio dei nomi Microsoft. VisualStudio. OLE. Interop) da compilare con i valori per ogni proprietà. La matrice deve contenere almeno `cpspec` elementi di dimensioni. Il chiamante non deve inizializzare i valori nella matrice.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se una o più proprietà non sono state trovate. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Se una proprietà non viene trovata, la voce corrispondente nella `rgvar` matrice contiene un oggetto `VARIANT` con il tipo di `VT_EMPTY` .

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)