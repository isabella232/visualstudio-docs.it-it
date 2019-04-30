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
ms.openlocfilehash: 71d4501fff04b62abe392c6684a4a0551dea9ee8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443659"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfaccia IWebAppDiagnosticsSetup
Questa interfaccia viene implementata da un'applicazione di debug PDM per creare oggetti COM nel processo di cui è in corso il debug e per abilitare la diagnostica web. Se PDM esegue il debug dell'applicazione oggetto implementa [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer chiama [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) dopo che è stato creato e passa un riferimento a [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Le chiamate di un'applicazione WWA [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) e passa il WWA interfaccia IWebApplicationHost invece. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato con un valore diverso da NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce true. Se non, restituisce false e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ottiene i documenti di testo che sono nascoste per il filtro specificato.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|