---
title: Funzione SccGetVersion | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b5c5e5e6035d6ce0b81ba747efa3cea65ab2f97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531894"
---
# <a name="sccgetversion-function"></a>Funzione SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [funzione SccGetVersion](https://docs.microsoft.com/visualstudio/extensibility/sccgetversion-function).  
  
Questa funzione Ottiene il numero di versione dell'API di plug-in controllo di origine supportate per il plug-in del controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `LONG` tipo di dati che contiene il numero di versione dell'API di plug-in controllo di origine supportati:  
  
|WORD|Descrizione|  
|----------|-----------------|  
|HIWORD|Versione principale|  
|LOWORD|Versione secondaria|  
  
## <a name="remarks"></a>Note  
 Ad esempio, se un controllo del codice sorgente del plug-in supporta la versione 1.3 dell'API dei plug-in controllo di origine, questa funzione restituirà 0x0103.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)

