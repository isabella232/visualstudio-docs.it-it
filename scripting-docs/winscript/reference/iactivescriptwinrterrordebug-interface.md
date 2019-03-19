---
title: Interfaccia IActiveScriptWinRTErrorDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60fbe5efe55b5347eb54eb4d6c010b6ab5903905
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144238"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>Interfaccia IActiveScriptWinRTErrorDebug
Implementato dal motore JavaScript per fornire informazioni di errore di Windows Runtime estese da un [enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md) evento. È possibile eseguire un QueryInterface per ottenerli da un' [IActiveScriptError](../../winscript/reference/iactivescripterror.md) oggetto.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IActiveScriptWinRTErrorDebug` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Restituisce la funzionalità di SID per l'errore di Runtime di Windows, se disponibile.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Restituisce il Runtime di Windows limitato stringa di riferimento di errore, se disponibile.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Restituisce il Runtime di Windows limitato stringa di errore, se disponibile.|