---
title: IWebAppDiagnosticsSetup::D iagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984577"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina se la diagnostica è supportata in questa applicazione. Se [è](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) stato chiamato il metodo per l'oggetto che implementa questa interfaccia con un valore non null, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce `true`. In caso contrario, restituisce `false` e le chiamate a [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) hanno esito negativo.  
  
> [!IMPORTANT]
> L' [interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata da PDM v 11.0 e versioni successive. Disponibile in activdbg100.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 Se [è](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) stato chiamato il metodo per l'oggetto che implementa questa interfaccia con un valore non null, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce `true`. In caso contrario, restituisce `false`e le chiamate a [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) hanno esito negativo.