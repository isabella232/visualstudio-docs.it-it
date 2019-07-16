---
title: Distribuzione dei tipi di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196876"
---
# <a name="deploying-project-types"></a>Distribuzione dei tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Installa un nuovo Sil aggregator di tipi di progetto (ProjectAggregator2. dll) e anche un pacchetto Windows Installer per la ridistribuzione (ProjectAggregator2.msi). È necessario usare il nuovo Sil aggregator per i tipi di progetto di codice gestito. ProjectAggregator2 funziona limitazioni alternative nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto Sil aggregator che impediscono il corretto funzionamento tipi di progetto di codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare al nuovo Sil aggregator.  
  
1. Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.  
  
2. Rimuovere eventuali file binari NativeHierarchyWrapper dalla configurazione.  
  
3. Aggiungere ProjectAggregator2.msi alla propria configurazione.
