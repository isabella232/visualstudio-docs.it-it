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
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574368"
---
# <a name="scriptlanguageversion-enumeration"></a>Enumerazione SCRIPTLANGUAGEVERSION
Specifica le possibili versioni di scripting.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Versione predefinita. Il valore integer è 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting versione 5,7. Il valore integer è 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting versione 5,8. Il valore integer è 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Versione massima. Il valore integer è 255.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)