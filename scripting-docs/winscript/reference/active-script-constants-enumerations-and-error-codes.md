---
title: Costanti, enumerazioni e codici di errore di script ActiveX | Microsoft Docs
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
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572718"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Costanti, enumerazioni e codici di errore dello script ActiveX
In questa sezione vengono descritte le enumerazioni e i codici di errore utilizzati nei motori di Windows Scripting.  
  
## <a name="constants"></a>Costanti  
  
|Costante|Descrizione|  
|--------------|-----------------|  
|[Costanti SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Specifica il tipo di thread.|  
  
## <a name="properties"></a>Proprietà  
  
|proprietà|Descrizione|  
|--------------|-----------------|  
|[Proprietà SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Utilizzato per specificare se il motore di scripting deve essere mantenuto completamente funzionante se sono presenti riferimenti in attesa.|  
  
## <a name="enumerations"></a>Enumerazioni  
  
|Enumerazione|Descrizione|  
|-----------------|-----------------|  
|[Enumerazione SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Tipo di Garbage Collection da eseguire.|  
|[Enumerazione SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Specifica le possibili versioni di scripting.|  
|[Enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Specifica lo stato di un motore di script.|  
|||  
|[Enumerazione SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Specifica lo stato di un thread in un motore di scripting.|  
|[Enumerazione SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Rappresenta l'evento di script che si sta tracciando. Utilizzato nel [metodo Metodo iactivescriptsitetraceinfo:: SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Enumerazione SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Rappresenta il modo in cui il controllo dell'interfaccia utente deve essere gestito.|  
|[Enumerazione SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Rappresenta il tipo di elemento dell'interfaccia utente. Utilizzato nel [Metodo IActiveScriptSiteUIControl:: GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Codici di errore  
  
|Codice di errore|Descrizione|  
|----------------|-----------------|  
|[Codice di errore SCRIPT_E_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Un errore di script viene propagato al chiamante, che potrebbe trovarsi in un thread diverso.|  
|[Codice di errore SCRIPT_E_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|È stato passato un errore tra il modulo di gestione di script e l'host.|  
|[Codice di errore SCRIPT_E_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Il motore di scripting ha segnalato un'eccezione non gestita all'host.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)