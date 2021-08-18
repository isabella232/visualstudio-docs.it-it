---
description: Legge le proprietà specificate dal set di proprietà corrente.
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: da6a492b30121a429b4c1ae5f5048b41cc9dcd8921e24a312dcc056371c8d211
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344924"
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

[in] Numero di proprietà specificate nella `rgpspec` matrice. Se zero, il metodo non restituisce proprietà, ma restituisce `S_OK` come codice di esito positivo.

 `rgpspec`

[in] Matrice di proprietà da leggere. Le proprietà possono essere specificate da un ID proprietà o da un nome di stringa facoltativo. Non è necessario specificare le proprietà in un ordine specifico nella matrice. La matrice può contenere proprietà duplicate, con conseguente valori di proprietà duplicati al ritorno per le proprietà semplici. Le proprietà non semplici devono restituire l'accesso negato al tentativo di aprirle una seconda volta. La matrice può contenere una combinazione di ID proprietà e ID stringa. Questa matrice deve avere almeno `cpspec` un numero di valori di proprietà.

 `rgvar`

[in, out] Matrice di strutture (nello spazio dei nomi `PROPVARIANT` Microsoft.VisualStudio.OLE.Interop) da riempire con i valori per ogni proprietà. La matrice deve avere dimensioni `cpspec` di almeno elementi. Il chiamante non deve inizializzare i valori nella matrice.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se una o più proprietà non sono stati trovati. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Se non è stata trovata una proprietà, la voce corrispondente nella `rgvar` matrice contiene un oggetto con il tipo `VARIANT` `VT_EMPTY` .

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
