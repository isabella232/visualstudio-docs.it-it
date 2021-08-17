---
title: Registrazione in MSBuild | Microsoft Docs
description: Informazioni su MSBuild di compilazione consente di monitorare lo stato di avanzamento della compilazione acquisendo eventi di compilazione, messaggi, avvisi ed errori in un file di log.
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
ms.openlocfilehash: 18d89ab73a019b06e11130b774b7db4d03ce1877bb53beeca18ba8fb037f5d0b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443263"
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
