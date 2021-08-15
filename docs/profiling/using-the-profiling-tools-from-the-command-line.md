---
title: Uso degli strumenti per la profilatura dalla riga di comando | Microsoft Docs
description: Usare gli strumenti da riga di comando di Visual Studio Strumenti di profilatura profilare le applicazioni e automatizzare la profilatura usando file batch e script.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 12c1a7b678983bce345d1c3af3a16852ea00be90000cc17d858d8be54a51c394
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270081"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Usare gli strumenti per la profilatura dalla riga di comando
È possibile usare gli strumenti da riga di comando degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire la profilatura di applicazioni dal prompt dei comandi e automatizzare la profilatura tramite file batch e script. È anche possibile generare file di report dal prompt dei comandi. È possibile usare il profiler autonomo leggero per raccogliere dati nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Impostare la posizione dei simboli:** Per visualizzare i nomi delle funzioni e dei parametri, il profiler deve avere accesso al simbolo (.*pdb*) dei file binari profilati. Questi file devono includere i file di simboli per il sistema operativo Microsoft e le applicazioni da visualizzare nell'analisi. È possibile usare il server di simboli Microsoft pubblico per assicurarsi di avere il corretto . *file pdb* per i file binari Microsoft. | -   [Procedura: Specificare i percorsi dei file di simboli dalla riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Eseguire la profilatura dell'applicazione:** gli strumenti e le opzioni della riga di comando usati per la profilatura di un'applicazione di destinazione dipendono dal tipo di applicazione, dal metodo di profilatura e dal fatto che la destinazione sia un'applicazione gestita o nativa. | -   [Usare i metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilare applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Servizi di profilare](../profiling/command-line-profiling-of-services.md) |
| **Creare report XML e CSV:** la profilatura dal prompt dei comandi crea file di dati che possono essere visualizzati nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È anche possibile generare . *valore xml* o delimitato da virgole (.*csv*) dei dati usando lo strumento da riga di comando VSPerfReport. | -   [Creare report del profiler dalla riga di comando](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [Vsperfreport](../profiling/vsperfreport.md) |
| **Eseguire la profilatura del codice nei computer senza Visual Studio:** è possibile usare il profiler autonomo degli strumenti di profilatura per raccogliere dati per le applicazioni nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. | -   [Procedura: Installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Riferimento
- [Informazioni di riferimento sulla riga Strumenti di profilatura comando](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Vedi anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
