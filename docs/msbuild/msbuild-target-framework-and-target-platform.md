---
title: Framework e piattaforma di destinazione di MSBuild | Microsoft Docs
description: Informazioni su come compilare un progetto MSBuild da eseguire in una versione .NET Framework di destinazione e in una piattaforma di destinazione o in un'architettura software.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: edc39690f057054092dc311709886187d0d1abdd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143092"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Framework e piattaforma di destinazione di MSBuild

È possibile compilare un progetto per eseguirlo in un *framework di destinazione*, che è una versione particolare di .NET Framework e una *piattaforma di destinazione*, che è un'architettura software particolare.  Ad esempio, è possibile impostare come destinazione un'applicazione da eseguire nel .NET Framework 2.0 in una piattaforma a 32 bit compatibile con la famiglia di processori 80x86 ("x86"). La combinazione di framework di destinazione e piattaforma di destinazione è nota come *contesto di destinazione*.

> [!IMPORTANT]
> Questo articolo descrive il metodo precedente per specificare un framework di destinazione. I progetti in stile SDK abilitano framework di destinazione diversi, ad esempio netstandard. Per altre informazioni, vedere [Framework di destinazione](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Profilo e framework di destinazione

 Un framework di destinazione è una versione particolare di .NET Framework in cui il proprio progetto è compilato per essere eseguito. La specifica di un framework di destinazione è necessaria perché abilita le funzionalità del compilatore e i riferimenti dell'assembly che sono esclusivi di quella versione di framework.

 Le versioni seguenti di .NET Framework sono attualmente disponibili per l'uso:

- .NET Framework 2.0 (incluso in Visual Studio 2005)

- La .NET Framework 3.0 (inclusa in Windows Vista)

- Il .NET Framework 3.5 (incluso in Visual Studio 2008)

- .NET Framework 4.5.2

- Il .NET Framework 4.6 (incluso in Visual Studio 2015)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Le versioni di .NET Framework sono diverse l'una dall'altra nell'elenco di assembly che ognuna rende disponibile come riferimento. Ad esempio, non è possibile compilare applicazioni WPF (Windows Presentation Foundation) a meno che il progetto non imposti .NET Framework versione 3.0 o versioni superiori come destinazione.

Il framework di destinazione viene specificato nella proprietà `TargetFrameworkVersion` nel file di progetto. È possibile modificare il framework di destinazione per un progetto usando le pagine di proprietà del progetto nell'ambiente di sviluppo integrato (IDE) di Visual Studio. Per altre informazioni, vedere [Procedura: Scegliere una versione di .NET Framework](../ide/visual-studio-multi-targeting-overview.md). I valori disponibili per `TargetFrameworkVersion` sono `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2` e `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 Un *profilo target* è un subset di un framework di destinazione. Ad esempio, Framework 4 Client Profile non include riferimenti agli assembly di MSBuild.

 > [!NOTE]
 > I profili di destinazione si applicano solo [alle librerie di classi portabili.](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library)

 Il framework di destinazione viene specificato nella proprietà `TargetFrameworkProfile` in un file di progetto. È possibile modificare il profilo target usando il controllo del framework di destinazione nelle pagine delle proprietà del progetto nell'IDE.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Piattaforma di destinazione

 Una *piattaforma* è una combinazione di hardware e software che definisce un particolare ambiente di runtime. Ad esempio,

- `x86` definisce un sistema operativo Windows a 32 bit che è in esecuzione su un processore 80x86 Intel o un suo equivalente.

- `x64`designa un sistema operativo Windows a 64 bit in esecuzione in un processore Intel x64 o nel relativo equivalente.

- `Xbox` definisce la piattaforma Microsoft Xbox 360.

Una *piattaforma di destinazione* è una particolare piattaforma in cui il proprio progetto è compilato per l'esecuzione. Il framework di destinazione viene specificato nella proprietà di compilazione `PlatformTarget` in un file di progetto. È possibile modificare la piattaforma di destinazione usando le pagine della proprietà del progetto o la **Gestione configurazione** nell'IDE.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

Una *configurazione di destinazione* è un subset di una piattaforma di destinazione. Ad esempio, la configurazione `x86` `Debug` non include la maggior parte delle ottimizzazioni di codice. La configurazione di destinazione viene specificata nella proprietà di compilazione `Configuration` in un file di progetto. È possibile modificare la configurazione di destinazione usando le pagine della proprietà del progetto o la **Gestione configurazione**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>Vedi anche

- [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)
