---
title: Distribuzione dei tipi di progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bed37260925d4961ed5b5b7d3e69d55169444ad
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497901"
---
# <a name="deploy-project-types"></a>Distribuire i tipi di progetto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Installa un nuovo Sil aggregator tipo di progetto (*ProjectAggregator2. dll*) e anche un pacchetto Windows Installer per la ridistribuzione (*ProjectAggregator2.msi*). È necessario usare il nuovo Sil aggregator per i tipi di progetto di codice gestito. ProjectAggregator2 consente di ovviare ai limiti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto Sil aggregator che impedisce che i tipi di progetto di codice gestito funziona correttamente. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare al nuovo Sil aggregator.  
  
1.  Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.  
  
2.  Rimuovere eventuali file binari NativeHierarchyWrapper dalla configurazione.  
  
3.  Aggiungere *ProjectAggregator2.msi* alla propria configurazione.