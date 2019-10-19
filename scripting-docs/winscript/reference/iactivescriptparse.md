---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561643"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Se il motore di Windows script consente l'aggiunta di codice di testo non elaborato gli scriptlet allo script o consente la valutazione del testo dell'espressione in fase di esecuzione, implementa l'interfaccia `IActiveScriptParse`. Per i linguaggi di scripting interpretati che non dispongono di un ambiente di creazione indipendente, ad esempio VBScript, questo fornisce un meccanismo alternativo (diverso da `IPersist*`) per ottenere il codice di script nel motore di script e per alleghi frammenti di script a vari eventi oggetto .  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inizializza il motore di scripting.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Aggiunge un scriptlet di codice allo script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analizza il codice scriptlet specificato, aggiungendo le dichiarazioni nello spazio dei nomi e valutando il codice nel modo appropriato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)