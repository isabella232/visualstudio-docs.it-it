---
title: Distribuzione di tipi di progetto | Microsoft Docs
description: Informazioni su come distribuire i tipi di progetto di codice gestito usando un nuovo aggregatore di tipi di progetto e Windows Installer pacchetto per la ridistribuzione in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1b015f29b6521482013a77bbcf7c44d8a79afa6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329876"
---
# <a name="deploy-project-types"></a>Distribuire i tipi di progetto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] consente di installare un nuovo aggregatore di tipi di progetto (*ProjectAggregator2.dll*) e anche un pacchetto di Windows Installer per la ridistribuzione (*ProjectAggregator2.msi*). È necessario usare il nuovo aggregatore per i tipi di progetto di codice gestito. ProjectAggregator2 funziona in base alle limitazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Project aggregator che impedisce il corretto funzionamento dei tipi di progetto di codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare il nuovo aggregatore.

1. Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.

2. Rimuovere tutti i file binari NativeHierarchyWrapper dalla configurazione.

3. Aggiungere *ProjectAggregator2.msi* alla configurazione.
