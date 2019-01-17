---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347645"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Se lo Script di Windows motore consente gli scriptlet di codice di testo non elaborato da aggiungere allo script oppure consente di testo dell'espressione deve essere valutata in fase di esecuzione, implementa la `IActiveScriptParse32` interfaccia. Nei linguaggi di scripting interpretati che non dispongono di alcun ambiente di creazione indipendente, ad esempio VBScript, si fornisce un meccanismo alternativo (diverso da `IPersist*`) per ottenere codice di script nel motore di scripting e collegare i frammenti di script per oggetti diversi eventi.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Aggiunge un scriptlet di codice allo script.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inizializza il motore di scripting.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analizza lo scriptlet di codice specificato, aggiungendo le dichiarazioni nello spazio dei nomi e la valutazione del codice come appropriato.|