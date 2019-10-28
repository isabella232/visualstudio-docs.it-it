---
title: 'IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984600"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Questo metodo crea una cocreazione della classe il cui ID viene passato con `rclsid` utilizzando il `dwClsContext`. Questa operazione è simile alla modalità di funzionamento di [IRemoteDebugApplication:: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) , con la differenza che nel caso di `CreateObjectWithSiteAtWebApp` l'oggetto viene creato in modo asincrono nel thread dell'interfaccia utente dell'applicazione Web. L'oggetto specificato dall'ID classe deve implementare l' [interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Dopo la creazione dell'oggetto, [IWebAppDiagnosticsObjectInitialization:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug PDM e il parametro `hPassToObject` di `CreateObjectWithSiteAtWebApp`. È possibile usare questo metodo per passare all'app un handle a una pipe anonima copiata usando [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> L' [interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata da PDM v 11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `rclsid`  
 ID classe della classe da creare.  
  
 `dwClsContext`  
 Contesto in cui il codice viene eseguito. Nella maggior parte dei casi è CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Non usato.  
  
 `hPassToObject`  
 Valore che verrà passato all'oggetto dopo che è stato creato nel thread dell'interfaccia utente, se l'oggetto implementa l' [interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).