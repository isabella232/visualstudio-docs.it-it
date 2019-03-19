---
title: Enumerazione SCRIPTLANGUAGEVERSION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144511"
---
# <a name="scriptlanguageversion-enumeration"></a>Enumerazione SCRIPTLANGUAGEVERSION
Specifica le possibili versioni di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|La versione predefinita. Il valore integer è 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting versione 5.7. Il valore intero è 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Versione 5.8 di Scripting di Windows. Il valore intero è 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Versione massima. Il valore intero è 255.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)