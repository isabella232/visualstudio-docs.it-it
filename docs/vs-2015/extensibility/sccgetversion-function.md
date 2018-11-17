---
title: Funzione SccGetVersion | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 16a21ab75c8390f0bb5ff5f016f2bf5b8d04c3a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779086"
---
# <a name="sccgetversion-function"></a>Funzione SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

