---
title: Interfaccia IActiveScriptParseProcedureOld | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 520d3f1414447abfc7c018d36853b72aefbbf15f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386162"
---
# <a name="iactivescriptparseprocedureold-interface"></a>Interfaccia IActiveScriptParseProcedureOld
Consente il testo del codice sorgente per le procedure da aggiungere allo script. Per i linguaggi di scripting interpretati che non è un ambiente di creazione indipendente, ad esempio VBScript, si fornisce un meccanismo alternativo (diverso da `IActiveScriptParse` o `IPersist*`) per aggiungere le procedure di script allo spazio dei nomi.  
  
> [!NOTE]
> Questa interfaccia è deprecata in favore del `IActiveScriptParseProcedure` interfaccia.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, il `IActiveScriptParseProcedureOld` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizza la procedura di codice specificato e aggiunge la procedura per lo spazio dei nomi.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)