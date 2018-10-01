---
title: Introduzione a Plug-in controllo codice sorgente | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56b38a1727d0ae859d12b1547e90705cdd6716e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529222"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introduzione ai plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Guida introduttiva a Plug-in controllo del codice sorgente](https://docs.microsoft.com/visualstudio/extensibility/internals/getting-started-with-source-control-plug-ins).  
  
Per creare un controllo del codice sorgente del plug-in, è necessario creare una DLL che implementa le funzioni definite nell'API di plug-in controllo di origine, quindi per registrare la DLL con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per renderlo disponibile per l'utilizzo nel controllo di versione del codice sorgente.  
  
 Tre versioni dell'API dei plug-in controllo di origine (versioni 1.1, 1.2 e 1.3) sono disponibili per plug-in controllo codice sorgente. L'API dei plug-in del controllo origine documentati qui è la versione 1.3. È stato progettato per essere completamente compatibili con plug-in controllo codice sorgente che supporta le versioni 1.1 e 1.2. Il [What ' s New nel plug-in origine controllo API versione 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) sezione illustra nel dettaglio le nuove funzionalità supportate nella versione più recente dell'API dei plug-in controllo di origine.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Procedura: Installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Viene descritto come rendere le voci del Registro di sistema necessari per inserire un controllo del codice sorgente DLL.  
  
 [Novità della versione 1.3 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fornisce una breve panoramica delle modifiche apportate all'API dei plug-in controllo di origine nella versione 1.3.  
  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fornisce una breve panoramica delle modifiche apportate all'API dei plug-in controllo di origine nella versione 1.2.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API dei plug-in controllo di origine.  
  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce il SDK dei plug-in controllo di origine e descritte le risorse incluse.

