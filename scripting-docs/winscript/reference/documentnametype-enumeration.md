---
title: Enumerazione DOCUMENTNAMETYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152483"
---
# <a name="documentnametype-enumeration"></a>Enumerazione DOCUMENTNAMETYPE
Descrive quale tipo richiedere per un documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Ottiene il nome visualizzato nell'albero dell'applicazione.|  
|DOCUMENTNAMETYPE_TITLE|Ottiene il nome visualizzato sulla barra del titolo del visualizzatore.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Ottiene il nome del file senza percorso.|  
|DOCUMENTNAMETYPE_URL|Ottiene l'URL del documento.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Ottiene il titolo con enumerazione per l'identificazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)