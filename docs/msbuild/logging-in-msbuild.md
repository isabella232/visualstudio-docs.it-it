---
title: Registrazione in MSBuild | Microsoft Docs
description: Informazioni su come MSBuild registrazione consente di monitorare lo stato di avanzamento della compilazione acquisendo eventi di compilazione, messaggi, avvisi ed errori in un file di log.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 673a46cb6727adcc1b9625187b5d7949cb07ea5a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625649"
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
