---
title: Interfaccia IActiveScriptErrorDebug110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067a62ec8b87c448577cfd6e5789ae5e073b5fb8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345903"
---
# <a name="iactivescripterrordebug110-interface"></a>Interfaccia IActiveScriptErrorDebug110
Aggiunge funzionalità per la [interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md). Questa interfaccia viene implementata dal motore JavaScript per determinare il motivo per cui si è verificato un evento BREAKREASON_ERROR.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IActiveScriptErrorDebug110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Restituisce il tipo di eccezione per un'eccezione generata.|