---
title: Profilatura di applicazioni autonome dalla riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcd48f421dcae74e82b0d9249a958f2a834f0a45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831681"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilatura di applicazioni autonome dalla riga di comando
Questa sezione descrive le procedure e le opzioni per la raccolta di dati sulle prestazioni per le applicazioni client autonome Web tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla riga di comando.

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuti correlati |
| - | - |
| **Raccogliere statistiche dell'applicazione:** usare il metodo di campionamento per raccogliere statistiche sulle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni. | -   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni. | -   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che indicano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection. | -   [Raccogliere dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Raccogliere dati di concorrenza:** usare il metodo di concorrenza per raccogliere i dati relativi alle contese di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché le contese e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema. | -   [Raccogliere dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati sulle prestazioni relative alle chiamate sincrone ADO.NET che l'applicazione ha eseguito nei confronti di un database Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. | -   [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Prova:** usare le procedure dettagliate per sottoporre a profilatura un'applicazione client di esempio tramite il metodo di campionamento o di strumentazione. | -   [Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Procedura dettagliata: Profilatura dalla riga di comando tramite strumentazione](/visualstudio/profiling/command-line-profiling-of-stand-alone-applications) |

## <a name="related-tasks"></a>Attività correlate

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Sottoporre a profilatura i servizi**|-   [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)|