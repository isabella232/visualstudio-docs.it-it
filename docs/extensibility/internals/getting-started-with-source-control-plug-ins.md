---
title: Attività iniziali con plug-in del controllo del codice sorgente | Microsoft Docs
description: Informazioni sulla creazione di un plug-in di controllo del codice sorgente che implementa le funzioni definite nell'API plug-in del controllo del codice sorgente per l'uso nel controllo della versione del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 676ef23c57569819e462e15c1d386c8cd0559933
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634580"
---
# <a name="get-started-with-source-control-plug-ins"></a>Introduzione ai plug-in del controllo del codice sorgente
Per creare un plug-in del controllo del codice sorgente, è necessario creare una DLL che implementa le funzioni definite nell'API plug-in del controllo del codice sorgente e quindi registrare la DLL con per renderla disponibile per l'uso nel controllo della versione del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente.

 Sono disponibili tre versioni dell'API plug-in del controllo del codice sorgente (versioni 1.1, 1.2 e 1.3) per i plug-in del controllo del codice sorgente. L'API plug-in del controllo del codice sorgente documentata qui è la versione 1.3. È stato progettato per essere completamente compatibile con i plug-in del controllo del codice sorgente che supportano le versioni 1.1 e 1.2. Nella [sezione Novità dell'API plug-in](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) del controllo del codice sorgente versione 1.3 vengono fornite informazioni dettagliate sulle nuove funzionalità supportate nella versione più recente dell'API plug-in del controllo del codice sorgente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: Installare un plug-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Viene descritto come creare le voci del Registro di sistema necessarie per collegare una DLL del controllo del codice sorgente.

- [Novità dell'API plug-in del controllo del codice sorgente versione 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Fornisce una breve panoramica delle modifiche apportate all'API plug-in del controllo del codice sorgente nella versione 1.3.

- [Novità dell'API plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Fornisce una breve panoramica delle modifiche apportate all'API plug-in del controllo del codice sorgente nella versione 1.2.

## <a name="related-sections"></a>Sezioni correlate
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)

 Fornisce un elenco completo di tutti gli elementi nell'API plug-in del controllo del codice sorgente.

- [Creare un plug-in del controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.
