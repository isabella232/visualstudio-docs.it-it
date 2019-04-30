---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Microsoft Docs
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
ms.openlocfilehash: 1d4214dea16c1e8a96ece7428f9ea73640025a9c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443668"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina se la diagnostica è supportata in questa applicazione. Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato sull'oggetto che implementa questa interfaccia con un valore diverso da NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce `true`. Se non viene restituito `false` e richiama [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.  
  
> [!IMPORTANT]
> [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata da PDM v11.0 e versioni successive. Vedere activdbg100.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 Se [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) è stato chiamato sull'oggetto che implementa questa interfaccia con un valore diverso da NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) restituisce `true`. Se non viene restituito `false`e le chiamate a [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) esito negativo.