---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575901"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Questa interfaccia viene implementata dagli host che supportano un'interfaccia utente sullo stesso oggetto di [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Gli host che non supportano un'interfaccia utente, ad esempio i server, non implementano l'interfaccia `IActiveScriptSiteWindow`. Il motore di script accede a questa interfaccia chiamando `QueryInterface` da `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera l'handle della finestra che può fungere da proprietario di una finestra popup che deve essere visualizzata dal motore di scripting.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Consente all'host di abilitare o disabilitare la finestra principale e le finestre di dialogo non modali.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)