---
title: Usare i set di impostazioni in applicazioni a più livelli | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657806"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Uso dei set di dati nelle applicazioni a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le applicazioni dati a più livelli * sono applicazioni incentrate sui dati separate in più livelli logici (o *livelli*). In altre parole, un'applicazione dati a più livelli è un'applicazione separata in più progetti, con il livello di accesso ai dati, il livello di logica di business e il livello di presentazione, ciascuno in un progetto distinto. Per altre informazioni, vedere [Panoramica delle applicazioni dati](../data-tools/n-tier-data-applications-overview.md)a più livelli.

 I dataset tipizzati sono stati migliorati in modo da poter generare classi TableAdapter e di dataset in progetti discreti, consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.

 Il supporto a più livelli nei dataset tipizzati consente lo sviluppo iterativo dell'architettura dell'applicazione in una progettazione a più livelli. Elimina inoltre la necessità di separare manualmente il codice in più di un progetto. Iniziare a progettare il livello dati usando il Progettazione DataSet. Prima di applicare l'architettura dell'applicazione in una progettazione a più livelli, impostare la proprietà **Progetto DataSet** di un set di dati per generare la classe di set di dati in un progetto separato.

## <a name="in-this-section"></a>Contenuto della sezione
 [Separare i set di impostazioni e i TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Viene descritto come spostare la classe DataSet generata fuori dal progetto che contiene le classi TableAdapter generate e in un nuovo progetto.

 [Aggiungere codice a oggetti TableAdapter in applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Viene descritto come generare una classe parziale in cui è possibile aggiungere codice per un TableAdapter a più livelli.

 [Aggiungere codice a DataSet in applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Viene descritto come generare una classe parziale in cui è possibile aggiungere codice per un set di dati a più livelli.

 [Aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md) Viene descritto dove aggiungere il codice per eseguire la convalida sulla modifica dei dati.

 [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Vengono fornite istruzioni dettagliate per la creazione di un DataSet tipizzato e la separazione del codice TableAdapter e del set di dati in più progetti.

 [Procedura dettagliata: aggiunta della convalida a un'applicazione dati a più livelli](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Vengono fornite istruzioni dettagliate per l'aggiunta della convalida all'applicazione creata nella procedura dettagliata relativa all'applicazione dati a più livelli.

## <a name="reference"></a>Riferimento
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Sezioni correlate

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Applicazioni a più livelli e remote con LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)