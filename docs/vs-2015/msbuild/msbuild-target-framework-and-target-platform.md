---
title: Framework e piattaforma di destinazione di MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a550b4a6634604594da0893e3f420fd9c38ca3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181035"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Framework e piattaforma di destinazione di MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile compilare un progetto per eseguirlo in un *framework di destinazione*, che è una versione particolare di .NET Framework e una *piattaforma di destinazione*, che è un'architettura software particolare.  Ad esempio, è possibile impostare un'applicazione come destinazione per eseguirla in .NET Framework 2.0 su una piattaforma a 32 bit compatibile con la famiglia di processori 802x86 ("x86"). La combinazione di framework di destinazione e piattaforma di destinazione è nota come *contesto di destinazione*.  
  
## <a name="target-framework-and-profile"></a>Profilo e framework di destinazione  
 Un framework di destinazione è una versione particolare di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in cui il proprio progetto è compilato per essere eseguito. La specifica di un framework di destinazione è necessaria perché abilita le funzionalità del compilatore e i riferimenti dell'assembly che sono esclusivi di quella versione di framework.  
  
 Le versioni seguenti di .NET Framework sono attualmente disponibili per l'uso:  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 (incluso in Visual Studio 2005)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0 (incluso in [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 (incluso in [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (incluso in Visual Studio 2010)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5 (incluso in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1 (incluso in [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6 (incluso in [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)])  
  
  Le versioni di .NET Framework sono diverse l'una dall'altra nell'elenco di assembly che ognuna rende disponibile come riferimento. Ad esempio, non è possibile compilare applicazioni WPF (Windows Presentation Foundation) a meno che il progetto non imposti .NET Framework versione 3.0 o versioni superiori come destinazione.  
  
  Il framework di destinazione viene specificato nella proprietà `TargetFrameworkVersion` nel file di progetto. È possibile modificare il framework di destinazione per un progetto usando le pagine di proprietà del progetto nell'ambiente di sviluppo integrato (IDE) di Visual Studio. Per altre informazioni, vedere [How to: target a version of the .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). I valori disponibili per `TargetFrameworkVersion` sono `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2` e `v4.6`.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 Un *profilo target* è un subset di un framework di destinazione. Ad esempio, Framework 4 Client Profile non include riferimenti agli assembly di MSBuild.  
  
 Il framework di destinazione viene specificato nella proprietà `TargetFrameworkProfile` in un file di progetto. È possibile modificare il profilo target usando il controllo del framework di destinazione nelle pagine delle proprietà del progetto nell'IDE. Per altre informazioni, vedere [How to: target a version of the .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Piattaforma di destinazione  
 Una *piattaforma* è una combinazione di hardware e software che definisce un particolare ambiente di runtime. Ad esempio:  
  
- `x86` definisce un sistema operativo Windows a 32 bit che è in esecuzione su un processore 80x86 Intel o un suo equivalente.  
  
- `Xbox` definisce la piattaforma Microsoft Xbox 360.  
  
  Una *piattaforma di destinazione* è una particolare piattaforma in cui il proprio progetto è compilato per l'esecuzione. Il framework di destinazione viene specificato nella proprietà di compilazione `Platform` in un file di progetto. È possibile modificare la piattaforma di destinazione usando le pagine della proprietà del progetto o la **Gestione configurazione** nell'IDE.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 Una *configurazione di destinazione* è un subset di una piattaforma di destinazione. Ad esempio, la configurazione `x86``Debug` non include la maggior parte delle ottimizzazioni di codice. La configurazione di destinazione viene specificata nella proprietà di compilazione `Configuration` in un file di progetto. È possibile modificare la configurazione di destinazione usando le pagine della proprietà del progetto o la **Gestione configurazione**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)
