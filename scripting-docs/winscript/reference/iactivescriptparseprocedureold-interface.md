---
title: Interfaccia IActiveScriptParseProcedureOld | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa7ea909680afdb65004f47e458d735e82ead929
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349993"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interfaccia IActiveScriptParseProcedureOld
Consente il testo del codice sorgente per le procedure da aggiungere allo script. Per i linguaggi di scripting interpretati che non è un ambiente di creazione indipendente, ad esempio VBScript, si fornisce un meccanismo alternativo (diverso da `IActiveScriptParse` o `IPersist*`) per aggiungere le procedure di script allo spazio dei nomi.  
  
> [!NOTE]
>  Questa interfaccia è deprecata in favore del `IActiveScriptParseProcedure` interfaccia.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, il `IActiveScriptParseProcedureOld` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizza la procedura di codice specificato e aggiunge la procedura per lo spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)