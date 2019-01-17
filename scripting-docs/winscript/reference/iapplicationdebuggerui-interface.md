---
title: Interfaccia IApplicationDebuggerUI | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3c5f9e4cabeb4fba31bb039a7cf673ca1759860
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348906"
---
# <a name="iapplicationdebuggerui-interface"></a>Interfaccia IApplicationDebuggerUI
Implementata dall'ambiente di sviluppo integrato (IDE) debugger (oltre a `IApplicationDebugger`) per offrire maggiore controllo sull'interfaccia utente (UI) del debugger di un componente esterno.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IApplicationDebuggerUI` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Visualizza la finestra che contiene il documento di debug specificato all'inizio nel debugger di interfaccia utente.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Visualizza la finestra che contiene il contesto del documento specificato nella parte superiore dell'interfaccia utente del debugger e consente di far scorrere la finestra nel contesto.|