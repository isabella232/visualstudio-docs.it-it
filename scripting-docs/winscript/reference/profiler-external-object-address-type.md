---
title: Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c9642a4a-f1fd-408a-9de6-e51562337bf1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ec2be5f35d15f0f7260e224b53ad4d8f07e8734
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347957"
---
# <a name="profilerexternalobjectaddress-type"></a>Tipo PROFILER_EXTERNAL_OBJECT_ADDRESS
L'indirizzo oggetto esterno di un oggetto, ad esempio un oggetto C++ con allocazione, che è all'esterno dell'heap JavaScript. Usato nel [struttura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e [struttura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef void* PROFILER_EXTERNAL_OBJECT_ADDRESS;  
```