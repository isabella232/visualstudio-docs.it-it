---
title: Distribuzione di tipi di progetto | Microsoft Docs
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
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708780"
---
# <a name="deploy-project-types"></a>Distribuire i tipi di progetto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] consente di installare un nuovo aggregatore di tipi di progetto (*ProjectAggregator2.dll*) e anche un pacchetto di Windows Installer per la ridistribuzione (*ProjectAggregator2.msi*). È necessario usare il nuovo aggregatore per i tipi di progetto di codice gestito. ProjectAggregator2 funziona in base alle limitazioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Project aggregator che impedisce il corretto funzionamento dei tipi di progetto di codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare il nuovo aggregatore.

1. Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.

2. Rimuovere tutti i file binari NativeHierarchyWrapper dalla configurazione.

3. Aggiungere *ProjectAggregator2.msi* alla configurazione.
