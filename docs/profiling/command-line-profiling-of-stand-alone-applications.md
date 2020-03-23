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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f80f3e65969973202af08299b07ebfa420f3bd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557862"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilatura della riga di comando di applicazioni autonome
Questa sezione descrive le procedure e le opzioni per la raccolta di dati sulle prestazioni per le applicazioni client autonome Web tramite gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla riga di comando.

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuti correlati |
| - | - |
| **Raccogliere statistiche delle applicazioni:** usare il metodo di campionamento per raccogliere statistiche delle prestazioni. I dati di campionamento sono utili per analizzare i problemi di utilizzo della CPU e comprendere le caratteristiche generali delle prestazioni delle applicazioni. | -   [Raccogliere statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Raccogliere dati di intervallo dettagliati:** usare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate. I dati di strumentazione sono utili per analizzare i problemi di I/O e per l'analisi dettagliata degli scenari delle applicazioni. | -   [Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Raccogliere dati di memoria .NET:** usare il campionamento o la strumentazione per raccogliere dati di allocazione della memoria .NET che illustrano le dimensioni e il numero di oggetti allocati. È anche possibile raccogliere dati sulla durata degli oggetti che mostrano le dimensioni e il numero di oggetti che vengono recuperati a ogni generazione di garbage collection. | -   [Raccogliere dati di memoria di .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Raccogliere dati di concorrenza:** usare il metodo di concorrenza per raccogliere i dati relativi ai conflitti di risorse e all'attività dei thread. Questi dati illustrano l'utilizzo della CPU, nonché i conflitti e la migrazione di thread, i ritardi nella sincronizzazione, le aree di sovrapposizione delle operazioni di I/O e altri eventi di sistema. | -   [Raccogliere dati di concorrenzaCollect concurrency data](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati sulle prestazioni relative alle chiamate sincrone ADO.NET che l'applicazione ha eseguito nei confronti di un database Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]. L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando. | -   [Raccogliere dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Attività correlate

|Attività|Contenuto correlato|
|----------|---------------------|
|**Sottoporre a profilatura applicazioni ASP.NET**|-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Sottoporre a profilatura i servizi**|-   [Servizi di profilo](../profiling/command-line-profiling-of-services.md)|
