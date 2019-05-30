---
title: Introduzione a Plug-in controllo codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71645c7e5334b24c294265a60581cc4a00eec8aa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328938"
---
# <a name="get-started-with-source-control-plug-ins"></a>Introduzione a plug-in controllo codice sorgente
Per creare un controllo del codice sorgente del plug-in, è necessario creare una DLL che implementa le funzioni definite nell'API di plug-in controllo di origine, quindi per registrare la DLL con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per renderlo disponibile per l'utilizzo nel controllo di versione del codice sorgente.

 Tre versioni dell'API dei plug-in controllo di origine (versioni 1.1, 1.2 e 1.3) sono disponibili per plug-in controllo codice sorgente. L'API dei plug-in del controllo origine documentati qui è la versione 1.3. È stato progettato per essere completamente compatibili con plug-in controllo codice sorgente che supporta le versioni 1.1 e 1.2. Il [nuove funzionalità di plug-in origine controllo API versione 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) sezione illustra nel dettaglio le nuove funzionalità supportate nella versione più recente dell'API dei plug-in controllo di origine.

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: Installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Viene descritto come rendere le voci del Registro di sistema necessari per inserire un controllo del codice sorgente DLL.

- [Quali sono le novità nella versione 1.3 di origine controllo plug-in di API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Fornisce una breve panoramica delle modifiche apportate all'API dei plug-in controllo di origine nella versione 1.3.

- [Novità di plug-in origine controllo API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Fornisce una breve panoramica delle modifiche apportate all'API dei plug-in controllo di origine nella versione 1.2.

## <a name="related-sections"></a>Sezioni correlate
- [Plug-in controllo codice sorgente](../../extensibility/source-control-plug-ins.md)

 Fornisce un elenco completo di tutti gli elementi nell'API dei plug-in controllo di origine.

- [Creare un controllo del codice sorgente del plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definisce il SDK dei plug-in controllo di origine e descritte le risorse incluse.