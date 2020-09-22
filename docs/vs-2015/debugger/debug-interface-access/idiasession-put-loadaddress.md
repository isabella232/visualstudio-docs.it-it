---
title: IDiaSession::put_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839264"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli nell'archivio simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `NewVal`  
 in Indirizzo di caricamento per il file eseguibile.  
  
## <a name="remarks"></a>Commenti  
 Le proprietà dell'indirizzo virtuale del simbolo (VA) vengono calcolate usando il valore di questo metodo. Gli indirizzi virtuali non vengono calcolati se questa proprietà non è impostata su un valore diverso da zero.  
  
> [!NOTE]
> È necessario chiamare questo metodo quando si ottiene l'oggetto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e prima di iniziare a usare l'oggetto se è necessario usare qualsiasi proprietà virtuale nei simboli.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
