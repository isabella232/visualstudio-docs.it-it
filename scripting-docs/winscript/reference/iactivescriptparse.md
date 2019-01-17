---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8325ffcb21f1871ca742611e6587df02ef3b89c8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349010"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Se lo Script di Windows motore consente gli scriptlet di codice di testo non elaborato da aggiungere allo script oppure consente di testo dell'espressione deve essere valutata in fase di esecuzione, implementa la `IActiveScriptParse` interfaccia. Nei linguaggi di scripting interpretati che non dispongono di alcun ambiente di creazione indipendente, ad esempio VBScript, si fornisce un meccanismo alternativo (diverso da `IPersist*`) per ottenere codice di script nel motore di scripting e collegare i frammenti di script per oggetti diversi eventi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inizializza il motore di scripting.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Aggiunge un scriptlet di codice allo script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analizza lo scriptlet di codice specificato, aggiungendo le dichiarazioni nello spazio dei nomi e la valutazione del codice come appropriato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)