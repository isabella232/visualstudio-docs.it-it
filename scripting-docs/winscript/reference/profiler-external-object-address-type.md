---
title: Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9642a4a-f1fd-408a-9de6-e51562337bf1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b5708dfb0ad5e419f217d6d06a3c2b039d55b35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831558"
---
# <a name="profilerexternalobjectaddress-type"></a>Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS
L'indirizzo oggetto esterno di un oggetto, ad esempio un oggetto C++ con allocazione, che è all'esterno dell'heap JavaScript. Usato nel [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef void* PROFILER_EXTERNAL_OBJECT_ADDRESS;  
```