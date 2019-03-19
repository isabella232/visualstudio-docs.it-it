---
title: Interfaccia IWebAppDiagnosticsSetup | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b84fd126ebd4d311264efa5d2156f9d83961fee9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148750"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfaccia IWebAppDiagnosticsSetup
Questa interfaccia viene implementata da un'applicazione di debug PDM per creare oggetti COM nel processo di cui è in corso il debug e per abilitare la diagnostica web. Se PDM esegue il debug dell'applicazione oggetto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer chiama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) dopo che è stato creato e passa un riferimento a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Le chiamate di un'applicazione WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) e passa il WWA interfaccia IWebApplicationHost invece. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato con un valore diverso da NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce true. Se non, restituisce false e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ottiene i documenti di testo che sono nascoste per il filtro specificato.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|