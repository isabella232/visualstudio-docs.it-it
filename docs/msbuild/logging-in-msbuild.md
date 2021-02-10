---
title: Registrazione in MSBuild | Microsoft Docs
description: Informazioni su come la registrazione di MSBuild fornisce un modo per monitorare lo stato di avanzamento della compilazione acquisendo eventi di compilazione, messaggi, avvisi ed errori in un file di log.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: afbb79e2ce8ebdccc68def6ca4c42fde85c11bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966253"
---
# <a name="logging-in-msbuild"></a>Registrazione a MSBuild

La registrazione consente di monitorare lo stato di avanzamento di una compilazione. La registrazione acquisisce eventi di compilazione, messaggi, avvisi ed errori in un file di log.

## <a name="in-this-section"></a>Contenuto della sezione

- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)

 Vengono descritti i vari aspetti della registrazione in MSBuild.

- [Logger di compilazione](../msbuild/build-loggers.md)

 Delinea i passaggi necessari per creare un logger a processore singolo.

- [Registrazione in un ambiente a più processori](../msbuild/logging-in-a-multi-processor-environment.md)

 Descrive come funziona la registrazione in un ambiente a più processori e i due modelli di registrazione a più processori.

- [Scrivere logger compatibili con più processori](../msbuild/writing-multi-processor-aware-loggers.md)

 Illustra come creare logger compatibili con più processori e come usare ConfigurableForwardingLogger.

- [Creare logger di inoltro](../msbuild/creating-forwarding-loggers.md)

 Illustra come creare logger di inoltro personalizzati.

## <a name="see-also"></a>Vedi anche

- [Compilare più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) Descrive come compilare più progetti più velocemente eseguendoli in parallelo.
