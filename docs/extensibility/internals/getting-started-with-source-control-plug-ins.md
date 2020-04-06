---
title: Guida introduttiva ai plug-in del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708339"
---
# <a name="get-started-with-source-control-plug-ins"></a>Introduzione ai plug-in del controllo del codice sorgente
Per creare un plug-in del controllo del codice sorgente, è necessario creare una DLL che implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le funzioni definite nell'API del plug-in del controllo del codice sorgente e quindi registrare la DLL con per renderla disponibile per l'utilizzo nel controllo della versione del codice sorgente.

 Sono disponibili tre versioni dell'API del plug-in del controllo del codice sorgente (versioni 1.1, 1.2 e 1.3) per i plug-in del controllo del codice sorgente. L'API del plug-in del controllo del codice sorgente documentata qui è la versione 1.3.The Source Control Plug-in API documented here is version 1.3. È stato progettato per essere completamente compatibile con i plug-in del controllo del codice sorgente che supportano le versioni 1.1 e 1.2. La sezione [Novità dell'API del plug-in](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) del controllo del codice sorgente versione 1.3 descrive in dettaglio le nuove funzionalità supportate nella versione più recente dell'API del plug-in del controllo del codice sorgente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Procedura: installare un plug-in del controllo del codice sorgenteHow to: Install a source control plug-in](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 Viene descritto come creare le voci del Registro di sistema necessarie per collegare una DLL del controllo del codice sorgente.

- [Novità dell'API del plug-in del controllo del codice sorgente versione 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 Fornisce una breve panoramica delle modifiche apportate all'API del plug-in del controllo del codice sorgente nella versione 1.3.

- [Novità dell'API del plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 Fornisce una breve panoramica delle modifiche apportate all'API del plug-in del controllo del codice sorgente nella versione 1.2.

## <a name="related-sections"></a>Sezioni correlate
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)

 Fornisce un elenco completo di tutti gli elementi nell'API del plug-in del controllo del codice sorgente.

- [Creare un plug-in del controllo del codice sorgenteCreate a source control plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)

 Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.
