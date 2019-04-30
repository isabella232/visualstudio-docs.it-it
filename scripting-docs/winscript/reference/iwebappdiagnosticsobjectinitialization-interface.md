---
title: Interfaccia IWebAppDiagnosticsObjectInitialization | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a992f8512d4927eeb58d6437ccb830abda688b28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443690"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>Interfaccia IWebAppDiagnosticsObjectInitialization
Questa interfaccia può essere implementata nelle classi che implementano [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) viene implementata dall'oggetto che implementa [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Nella maggior parte dei casi questo oggetto è PDM.  
  
 Dopo aver creato l'oggetto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug PDM e il `hPassToObject` parametro `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsObjectInitialization` viene rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inizializza l'oggetto.|