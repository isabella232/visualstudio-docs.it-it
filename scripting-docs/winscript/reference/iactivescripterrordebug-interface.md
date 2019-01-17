---
title: Interfaccia IActiveScriptErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d773724d23c61aa72b8cd48917f2cd0bef4a7cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345201"
---
# <a name="iactivescripterrordebug-interface"></a>Interfaccia IActiveScriptErrorDebug
Fornisce informazioni sul contesto di documento per le eccezioni di runtime ed errori in fase di compilazione. Il `IActiveScriptError::QueryInterface` metodo supporta il `IActiveScriptErrorDebug` interfaccia.  
  
 Oltre ai metodi ereditati da `IActiveScriptError`, il `IActiveScriptErrorDebug` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fornisce il contesto di documento per questo errore.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fornisce lo stack frame che è attiva per gli errori di runtime.|