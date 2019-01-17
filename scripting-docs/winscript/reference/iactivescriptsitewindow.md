---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a160b17f4a46237ab78b378664a046fe8a0e7d4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345721"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Questa interfaccia viene implementata dagli host che supportano un'interfaccia utente sullo stesso oggetto come [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Gli host che non supportano un'interfaccia utente, ad esempio i server, non implementare il `IActiveScriptSiteWindow` interfaccia. Il motore di scripting accede a questa interfaccia mediante la chiamata `QueryInterface` da `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera l'handle della finestra che può agire come proprietario di una finestra popup in cui il motore di script deve essere visualizzati.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Fa sì che l'host abilitare o disabilitare la finestra principale, nonché eventuali finestre di dialogo non modale.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)