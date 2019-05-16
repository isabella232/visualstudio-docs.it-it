---
title: Lavorare con i set di dati nelle applicazioni a n livelli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0459168da627b8e67ad669486b70eb7758118d92
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688198"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Uso dei set di dati nelle applicazioni a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le applicazioni dati a più livelli * sono applicazioni mirate ai dati separate in più livelli logici (o *livelli*). In altre parole, un'applicazione dati a più livelli è un'applicazione separata in più progetti, con il livello di accesso ai dati, il livello di logica di business e il livello di presentazione, ciascuno in un progetto distinto. Per altre informazioni, vedere [panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md).  
  
 I dataset tipizzati sono stati migliorati in modo da poter generare classi TableAdapter e di dataset in progetti discreti, consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.  
  
 Supporto a più livelli nei dataset tipizzati consente lo sviluppo iterativo dell'architettura dell'applicazione in una progettazione a più livelli. Inoltre, si elimina la necessità di separare manualmente il codice in più di un progetto. Avviare la progettazione del livello dati usando la finestra di progettazione set di dati. Prima di applicare l'architettura dell'applicazione in una progettazione a più livelli, impostare la proprietà **Progetto DataSet** di un set di dati per generare la classe di set di dati in un progetto separato.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Descrive come spostare la classe di dataset generata dal progetto contenente le classi TableAdapter generate in un nuovo progetto.  
  
 [Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Descrive come generare una classe parziale in cui aggiungere il codice per una classe TableAdapter a più livelli.  
  
 [Aggiungere il codice nei set di dati di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Descrive come generare una classe parziale in cui aggiungere il codice per un dataset a più livelli.  
  
 [Aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Descrive dove aggiungere il codice per eseguire la convalida sulla modifica dei dati.  
  
 [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Fornisce istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice degli elementi TableAdapter e dataset in più progetti.  
  
 [Procedura dettagliata: Aggiunta della convalida a un'applicazione dati a più livelli](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Vengono fornite istruzioni dettagliate per l'aggiunta di convalida per l'applicazione è stata creata nella procedura dettagliata dell'applicazione dati a più livelli.  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Sezioni correlate

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)   
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
- [Applicazioni a più livelli e remote con LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)