---
title: Script ActiveX costanti, enumerazioni e codici di errore | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 090b494e904fbef1c0d3d8b380f7a184a6042788
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953998"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Costanti, enumerazioni e codici di errore dello script ActiveX
Questa sezione descrive le enumerazioni e codici di errore utilizzati nei motori di Scripting di Windows.  
  
## <a name="constants"></a>Costanti  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costanti SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Specifica il tipo di thread.|  
  
## <a name="properties"></a>Proprietà  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Consente di specificare se il motore di scripting deve essere mantenuto pienamente funzionale se sono presenti riferimenti in sospeso.|  
  
## <a name="enumerations"></a>Enumerazioni  
  
|Enumerazione|Descrizione|  
|-----------------|-----------------|  
|[Enumerazione SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Il tipo di garbage collection da eseguire.|  
|[Enumerazione SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Specifica le possibili versioni di script.|  
|[Enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Specifica lo stato di un motore di scripting.|  
|||  
|[Enumerazione SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Specifica lo stato di un thread in un motore di scripting.|  
|[Enumerazione SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Rappresenta l'evento di script che si sta tracciando. Utilizzato nel [metodo iactivescriptsitetraceinfo:: Sendscripttraceinfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Enumerazione SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Rappresenta il modo che il controllo dell'interfaccia utente deve essere gestito.|  
|[Enumerazione SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Rappresenta il tipo di elemento dell'interfaccia utente. Utilizzato nel [metodo iactivescriptsiteuicontrol:: Getuibehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Codici di errore  
  
|Codice di errore|Descrizione|  
|----------------|-----------------|  
|[Codice di errore SCRIPT_E_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Un errore di script viene propagato al chiamante, che potrebbe trovarsi in un altro thread.|  
|[Codice di errore SCRIPT_E_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Un errore è stato passato tra il motore di script e l'host.|  
|[Codice di errore SCRIPT_E_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Il motore di script ha rilevato un'eccezione non gestita nell'host.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)