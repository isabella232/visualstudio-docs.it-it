---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
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
ms.openlocfilehash: 26403a168268e817644637544d64d4205c398b75
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157659"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Questo metodo CO-crea la classe il cui ID è passare con `rclsid` utilizzando il `dwClsContext`. È simile al modo in cui [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) works, tranne che nel caso di `CreateObjectWithSiteAtWebApp` l'oggetto viene creato in modo asincrono nel thread dell'interfaccia utente dell'applicazione web. L'oggetto specificato dall'ID di classe deve implementare [interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Dopo aver creato l'oggetto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug PDM e il `hPassToObject` parametro `CreateObjectWithSiteAtWebApp`. È possibile usare questo metodo per passare all'App un handle di un'unnamed pipe che è stata copiata usando [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata da PDM v11.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `rclsid`  
 L'ID di classe della classe da creare.  
  
 `dwClsContext`  
 Il contesto in cui verrà eseguito il codice. Nella maggior parte dei casi è CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Non usato.  
  
 `hPassToObject`  
 Un valore che verrà passato all'oggetto dopo averla creata sul thread dell'interfaccia utente, se l'oggetto implementa [interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).