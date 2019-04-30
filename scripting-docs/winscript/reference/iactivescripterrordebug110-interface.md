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
ms.openlocfilehash: 72f545f5a48fc7b8aa3f9250b13a62ba659e94bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436062"
---
# <a name="iactivescripterrordebug110-interface"></a>Interfaccia IActiveScriptErrorDebug110
Aggiunge funzionalità per la [interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md). Questa interfaccia viene implementata dal motore JavaScript per determinare il motivo per cui si è verificato un evento BREAKREASON_ERROR.  
  
> [!IMPORTANT]
> Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IActiveScriptErrorDebug110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Restituisce il tipo di eccezione per un'eccezione generata.|