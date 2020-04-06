---
title: Distribuzione dei tipi di progetto Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708780"
---
# <a name="deploy-project-types"></a>Distribuire i tipi di progettoDeploy project types
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]installa un nuovo aggregatore di tipo di progetto (*ProjectAggregator2.dll*) e anche un pacchetto di Windows Installer per la ridistribuzione (*ProjectAggregator2.msi*). È necessario utilizzare il nuovo aggregatore per i tipi di progetto di codice gestito. ProjectAggregator2 aggira le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] limitazioni nell'aggregatore del progetto che impedisce il corretto funzionamento dei tipi di progetto con codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare il nuovo aggregatore.

1. Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.

2. Rimuovere tutti i file binari NativeHierarchyWrapper dall'installazione.

3. Aggiungere *ProjectAggregator2.msi* alla configurazione.
