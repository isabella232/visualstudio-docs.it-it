---
title: Interfaccia IWebAppDiagnosticsObjectInitialization | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c892d3eceea65f16c69bfd2202b1f64181773532
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348048"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>Interfaccia IWebAppDiagnosticsObjectInitialization
Questa interfaccia può essere implementata nelle classi che implementano [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata dall'oggetto che implementa [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Nella maggior parte dei casi questo oggetto è PDM.  
  
 Dopo aver creato l'oggetto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug PDM e il `hPassToObject` parametro `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` viene rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inizializza l'oggetto.|