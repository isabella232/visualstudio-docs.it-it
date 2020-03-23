---
title: Uso degli strumenti per la profilatura dalla riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1420aa9f92e8ef7564478499c78393510ad61c23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778037"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Usare gli strumenti per la profilatura dalla riga di comando
È possibile usare gli strumenti da riga di comando degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire la profilatura di applicazioni dal prompt dei comandi e automatizzare la profilatura tramite file batch e script. È anche possibile generare file di report dal prompt dei comandi. È possibile usare il profiler autonomo leggero per raccogliere dati nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Attività comuni

| Attività | Contenuto correlato |
| - | - |
| **Impostare la posizione dei simboli:** Per visualizzare i nomi di funzioni e parametri, il profiler deve avere accesso al simbolo (.* pdb*) dei file binari profilati. Questi file devono includere i file di simboli per il sistema operativo Microsoft e le applicazioni da visualizzare nell'analisi. È possibile utilizzare il server di simboli Microsoft pubblico per assicurarsi di disporre del file . *file pdb* per i file binari Microsoft. | -   [Procedura: specificare i percorsi dei file di simboli dalla riga di comandoHow to: Specify symbol file locations from the command line](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Eseguire la profilatura dell'applicazione:** gli strumenti e le opzioni della riga di comando usati per la profilatura di un'applicazione di destinazione dipendono dal tipo di applicazione, dal metodo di profilatura e dal fatto che la destinazione sia un'applicazione gestita o nativa. | -   [Usare i metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilare applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Servizi di profilo](../profiling/command-line-profiling-of-services.md) |
| **Creare report XML e CSV:** la profilatura dal prompt dei comandi crea file di dati che possono essere visualizzati nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È inoltre possibile generare . *xml* o valori delimitati da virgole (.* csv*) dei dati utilizzando lo strumento da riga di comando VSPerfReport. | -   [Creare report del profiler dalla riga di comando](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Eseguire la profilatura del codice nei computer senza Visual Studio:** è possibile usare il profiler autonomo degli strumenti di profilatura per raccogliere dati per le applicazioni nei computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. | -   [Procedura: installare il profiler autonomoHow to: Install the stand-alone profiler](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Informazioni di riferimento
- [Informazioni di riferimento per gli strumenti di profilatura della riga di comandoCommand-line Profiling Tools reference](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Vedere anche
- [Esplora prestazioni](../profiling/performance-explorer.md)
