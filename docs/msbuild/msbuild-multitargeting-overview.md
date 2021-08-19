---
title: Panoramica del multitargeting di MSBuild | Microsoft Docs
description: Informazioni su come usare MSBuild compilare un'applicazione da eseguire in una delle diverse versioni del .NET Framework e in una delle diverse piattaforme di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a71c3c774e512d012b1f1bbd99a8e00aa1304cda
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136846"
---
# <a name="msbuild-multitargeting-overview"></a>Panoramica del multitargeting di MSBuild

Tramite MSBuild è possibile compilare un'applicazione da eseguire in una qualunque delle tante versioni di .NET Framework e in una qualunque delle tante piattaforme di sistema. Ad esempio, è possibile compilare un'applicazione da eseguire in .NET Framework 2.0 in una piattaforma a 32 bit e compilare la stessa applicazione da eseguire in .NET Framework 4.5 in una piattaforma a 64 bit.

> [!IMPORTANT]
> Nonostante il nome "multitargeting", un progetto può essere destinato a un solo framework e a una sola piattaforma per volta.

 Di seguito sono riportate alcune delle funzionalità di definizione destinazione di MSBuild:

- È possibile sviluppare applicazioni destinate a una precedente versione di .NET Framework, ad esempio le versioni 2.0, 3.5 e 4.

- È possibile avere un framework di destinazione diverso da .NET Framework, ad esempio Silverlight.

- L'applicazione può essere destinata a un *profilo del framework*, vale a dire un subset predefinito di un framework di destinazione.

- In caso di rilascio di un Service Pack per la versione corrente di .NET Framework, è possibile destinare l'applicazione a esso.

- Il multitargeting di MSBuild garantisce che un'applicazione usi solo le funzionalità disponibili nel framework e nella piattaforma di destinazione.

## <a name="target-framework-and-platform"></a>Framework e piattaforma di destinazione

 Un *framework di destinazione* è la versione di .NET Framework per la quale un progetto è stato compilato appositamente e una *piattaforma di destinazione* è la piattaforma di sistema per la quale il progetto è stato compilato appositamente.  È ad esempio possibile scegliere come destinazione un'applicazione .NET Framework 2.0 per l'esecuzione in una piattaforma a 32 bit compatibile con la famiglia di processori 80x86 (x86). La combinazione di framework di destinazione e piattaforma di destinazione è nota come *contesto di destinazione*. Per altre informazioni, vedere [Framework e piattaforma di destinazione](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Set di strumenti (ToolsVersion)

 Un set di strumenti comprende strumenti, attività e destinazioni usati per creare l'applicazione. Un set di strumenti include compilatori come *csc.exe* *evbc.exe*, il file di destinazioni comuni (*microsoft.common.targets*) e il file delle attività comuni (*microsoft.common.tasks*). Il Set di strumenti 4.5 può essere usato per definire le destinazioni di .NET Framework versioni 2.0, 3.0, 3.5, 4 e 4.5. Tuttavia, il Set di strumenti 2.0 consente soltanto di scegliere come destinazione .NET Framework versione 2.0. Per altre informazioni, vedere [Set di strumenti MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Assembly di riferimento

 Gli assembly di riferimento specificati nel set di strumenti aiutano a progettare e sviluppare un'applicazione. Questi assembly di riferimento non solo consentono una specifica compilazione delle destinazioni, ma limitano anche i componenti e le funzionalità dell'IDE di Visual Studio a quelli compatibili con la destinazione. Per altre informazioni, vedere [Risoluzione di assembly in fase di progettazione](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Configurare destinazioni e attività

 È possibile configurare le destinazioni e le attività di MSBuild per l'esecuzione out-of-process con MSBuild, in modo che si possano scegliere come destinazione contesti notevolmente diversi da quello corrente.  Ad esempio, è possibile scegliere come destinazione un'applicazione .NET Framework 2.0 a 32 bit mentre nel computer di sviluppo è in esecuzione .NET Framework 4.5 su una piattaforma a 64 bit. Per altre informazioni, vedere [Configurazione di destinazioni e attività](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Risoluzione dei problemi

 Possono verificarsi errori se si tenta di fare riferimento a un assembly che non fa parte del contesto di destinazione. Per altre informazioni su questi errori e su come agire al riguardo, vedere [Risolvere i problemi relativi agli errori di impostazione di .NET Framework come destinazione](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
