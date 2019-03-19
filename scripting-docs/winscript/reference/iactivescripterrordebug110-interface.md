---
title: Interfaccia IActiveScriptErrorDebug110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1bac0c15f31f12ae48f6669bf9a0853550f8c191
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150647"
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