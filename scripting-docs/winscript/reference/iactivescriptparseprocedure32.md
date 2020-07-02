---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 16d432b6c150b53fdd059a48cc683d240bd1a50a
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835303"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Se il modulo di gestione di Windows script consente di aggiungere allo script il testo del codice sorgente per le procedure, implementa l' `IActiveScriptParseProcedure32` interfaccia. Per i linguaggi di scripting interpretati che non dispongono di un ambiente di creazione indipendente, ad esempio VBScript, questo fornisce un meccanismo alternativo (diverso da `IActiveScriptParse32` o `IPersist` *) per aggiungere procedure script allo spazio dei nomi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analizza la routine di codice specificata e aggiunge la routine allo spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)