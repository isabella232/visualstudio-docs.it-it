---
title: Distribuzione di Project tipi | Microsoft Docs
description: Informazioni su come distribuire tipi di progetto di codice gestito usando un nuovo aggregatore di tipo progetto e un pacchetto del programma di installazione di Windows per la ridistribuzione, in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7b3cacbb9a816171209cc5f1cbdd87ed4a1d7a7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086638"
---
# <a name="deploy-project-types"></a>Distribuire tipi di progetto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]installa un nuovo aggregatore di tipo progetto (*ProjectAggregator2.dll*) e un pacchetto Windows Installer per la ridistribuzione (*ProjectAggregator2.msi*). È necessario usare il nuovo aggregatore per i tipi di progetto di codice gestito. ProjectAggregator2 aggira le limitazioni dell'aggregatore di progetti che impediscono il corretto funzionamento dei tipi di progetto di codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestito. La procedura seguente descrive come modificare il pacchetto VSPackage per usare il nuovo aggregatore.

1. Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.

2. Rimuovere tutti i file binari NativeHierarchyWrapper dal programma di installazione.

3. Aggiungere *ProjectAggregator2.msi* configurazione.
