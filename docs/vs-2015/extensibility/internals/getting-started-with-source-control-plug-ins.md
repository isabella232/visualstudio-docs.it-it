---
title: Introduzione a Plug-in controllo codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85aa5727f252ad75c45064d7b885e3d282da36a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967256"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introduzione ai plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
