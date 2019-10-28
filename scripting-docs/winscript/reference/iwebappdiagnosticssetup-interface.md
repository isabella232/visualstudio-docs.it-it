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
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984545"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfaccia IWebAppDiagnosticsSetup
Questa interfaccia viene implementata da un'applicazione di debug PDM per creare oggetti COM nel processo di cui è in corso il debug e per abilitare la diagnostica Web. Se l'oggetto dell'applicazione di debug PDM implementa [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), Internet Explorer chiama il [sito](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) a sua volta dopo che è stato creato e passa un riferimento a [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Un'applicazione WWA chiama il [sito](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) e passa invece l'interfaccia WWA IWebApplicationHost. Se [il](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) metodo è stato chiamato con un valore diverso da null, [IWebAppDiagnosticsSetup::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce true. In caso contrario, restituisce false e le chiamate a [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) hanno esito negativo.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` viene implementato da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ottiene i documenti di testo nascosti dal filtro specificato.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Determina se il documento specificato appartiene a uno dei nodi figlio di questo nodo.|