---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200294"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Elimina un'istanza della `VsgDbg` classe. Se le informazioni grafiche vengono registrate attivamente, il file di log di grafica viene finalizzato e chiuso e le risorse utilizzate durante l'acquisizione attiva delle informazioni grafiche vengono rilasciate.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::VsgDbg (costruttore)](../debugger/vsgdbg-vsgdbg-constructor.md)
