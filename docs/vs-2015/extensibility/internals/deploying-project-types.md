---
title: Distribuzione di tipi di progetto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196876"
---
# <a name="deploying-project-types"></a>Distribuzione dei tipi di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] consente di installare un nuovo aggregatore di tipi di progetto (ProjectAggregator2.dll) e anche un pacchetto di Windows Installer per la ridistribuzione (ProjectAggregator2.msi). È necessario usare il nuovo aggregatore per i tipi di progetto di codice gestito. ProjectAggregator2 funziona in base alle limitazioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Project aggregator che impediscono il corretto funzionamento dei tipi di progetto di codice gestito. I passaggi seguenti descrivono come modificare il pacchetto VSPackage per usare il nuovo aggregatore.  
  
1. Rimuovere il progetto NativeHierarchyWrapper dalla soluzione.  
  
2. Rimuovere tutti i file binari NativeHierarchyWrapper dalla configurazione.  
  
3. Aggiungere ProjectAggregator2.msi alla configurazione.
