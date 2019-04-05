---
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965366"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Operazioni di lettura specificata delle proprietà dal set di proprietà corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cpspec`  
 [in] Conteggio delle proprietà specificate nel `rgpspec` matrice. Se è zero, il metodo non restituisce nessuna proprietà ma restituire `S_OK` come un codice di riuscita.  
  
 `rgpspec`  
 [in] Una matrice di proprietà da leggere. Le proprietà possono essere specificate da un ID di proprietà o da un nome di stringa facoltativa. Non è necessario specificare le proprietà in un ordine specifico nella matrice. La matrice può contenere proprietà duplicate, generando i valori delle proprietà duplicate nell'output restituito per le proprietà semplici. Proprietà semplice non deve restituire l'accesso negato nel tentativo di aprirli una seconda volta. La matrice può contenere una combinazione di ID di proprietà e ID di stringa. Questa matrice deve avere almeno `cpspec` numero dei valori delle proprietà.  
  
 `rgvar`  
 [in, out] Matrice di `PROPVARIANT` strutture (nello spazio dei nomi Interop) da compilare con i valori per ogni proprietà. La matrice deve essere almeno `cpspec` le dimensioni degli elementi. Il chiamante non necessita inizializzare i valori nella matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se uno o più delle proprietà non è stato trovato. In caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se una proprietà non trovato, la voce corrispondente nel `rgvar` matrice contiene una `VARIANT` con il tipo di `VT_EMPTY`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
