---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 10cdff328216d06a3326dd3595ef8fc78bc9cfc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348113"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Se il motore di Windows Script consente il testo del codice sorgente per le procedure da aggiungere allo script, implementa la `IActiveScriptParseProcedure32` interfaccia. Nei linguaggi di scripting interpretati che non dispongono di alcun ambiente di creazione indipendente, ad esempio VBScript, si fornisce un meccanismo alternativo (diverso da `IActiveScriptParse32` o `IPersist`*) per aggiungere le procedure di script allo spazio dei nomi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analizza la procedura di codice specificato e aggiunge la procedura per lo spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)