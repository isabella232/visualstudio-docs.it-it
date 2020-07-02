---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835316"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Se il motore di Windows script consente l'aggiunta di codice di testo non elaborato gli scriptlet allo script o consente la valutazione del testo dell'espressione in fase di esecuzione, implementa l' `IActiveScriptParse32` interfaccia. Per i linguaggi di scripting interpretati che non dispongono di un ambiente di creazione indipendente, ad esempio VBScript, questo fornisce un meccanismo alternativo (diverso da `IPersist*` ) per ottenere il codice di script nel motore di scripting e per alleghi frammenti di script a vari eventi dell'oggetto.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Aggiunge un scriptlet di codice allo script.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Inizializza il motore di scripting.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analizza il codice scriptlet specificato, aggiungendo le dichiarazioni nello spazio dei nomi e valutando il codice nel modo appropriato.|