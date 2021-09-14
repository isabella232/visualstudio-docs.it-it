---
title: Uso dei set di dati nelle applicazioni a più livelli
description: Informazioni su come usare i set di dati in applicazioni a più livelli. Le applicazioni dati a più livelli sono app incentrate sui dati separate in più livelli logici( o livelli).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1b3873b3348c78462943204b02f570a5510e927f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631014"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Uso dei set di dati nelle applicazioni a più livelli

*Le applicazioni dati a più livelli* sono applicazioni incentrate sui dati separate in più livelli logici *(o livelli*). In altre parole, un'applicazione dati a più livelli è un'applicazione separata in più progetti, con il livello di accesso ai dati, il livello di logica di business e il livello di presentazione, ciascuno in un progetto distinto. Per altre informazioni, vedere [Panoramica delle applicazioni dati a più livelli.](../data-tools/n-tier-data-applications-overview.md)

I dataset tipizzati sono stati migliorati in modo da poter generare classi TableAdapter e di dataset in progetti discreti, consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.

Il supporto a più livelli nei set di dati tipizzati consente lo sviluppo iterativo dell'architettura dell'applicazione in una progettazione a più livelli. Rimuove anche la necessità di separare manualmente il codice in più di un progetto. Iniziare a progettare il livello dati usando il **Progettazione DataSet**. Prima di applicare l'architettura dell'applicazione in una progettazione a più livelli, impostare la proprietà **Progetto DataSet** di un set di dati per generare la classe di set di dati in un progetto separato.

## <a name="reference"></a>Riferimento

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Vedi anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Aggiungere il codice nei set di dati di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [Applicazioni remote e a più livelli con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
