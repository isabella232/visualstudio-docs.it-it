---
title: Introduzione con i plug-in del controllo del codice sorgente | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538161"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introduzione ai plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per creare un plug-in del controllo del codice sorgente, è necessario creare una DLL che implementi le funzioni definite nell'API del plug-in del controllo del codice sorgente e quindi registrare la DLL con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per renderla disponibile per l'utilizzo nel controllo della versione del codice sorgente.  
  
 Sono disponibili tre versioni dell'API del plug-in del controllo del codice sorgente (versioni 1,1, 1,2 e 1,3) per i plug-in del controllo del codice sorgente. L'API del plug-in del controllo del codice sorgente documentata qui è la versione 1,3. È stato progettato per essere completamente compatibile con i plug-in del controllo del codice sorgente che supportano le versioni 1,1 e 1,2. La sezione novità della sezione [API del plug-in del controllo del codice sorgente versione 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) illustra le nuove funzionalità supportate nella versione più recente dell'API del plug-in del controllo del codice sorgente.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: Installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Viene descritto come creare le voci del registro di sistema necessarie per inserire una DLL del controllo del codice sorgente.  
  
 [Novità della versione 1.3 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Viene fornita una breve panoramica delle modifiche apportate all'API del plug-in del controllo del codice sorgente nella versione 1,3.  
  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Viene fornita una breve panoramica delle modifiche apportate all'API del plug-in del controllo del codice sorgente nella versione 1,2.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API del plug-in del controllo del codice sorgente.  
  
 [Creazione di un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.
