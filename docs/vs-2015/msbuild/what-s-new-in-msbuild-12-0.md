---
title: Novità di MSBuild 12.0 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d91ec9044461cf57bba8bb36a0d2e029635155c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540749"
---
# <a name="what39s-new-in-msbuild-120"></a>Novità di MSBuild 12.0
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](https://docs.microsoft.com/visualstudio/).  
  
MSBuild viene ora installato come parte di Visual Studio anziché di .NET Framework. Il numero di versione di MSBuild corrente è 12.0. Per installare MSBuild separatamente, scaricare il pacchetto di installazione dalla pagina di [download di MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  
  
## <a name="changed-path"></a>Percorso modificato  
 MSBuild viene ora installato direttamente in *%ProgramFiles%*, ad esempio in C:\Programmi\MSBuild\\\.  
  
## <a name="changed-properties"></a>Proprietà modificate  
 Come conseguenza del nuovo numero di versione sono state modificate le seguenti proprietà di MSBuild:  
  
-   `MSBuildToolsVersion` per questa versione degli strumenti è 12.0.  
  
-   `MSBuildToolsPath` è ora %Programmi%\MSBuild\12.0\bin nei sistemi operativi a 32 bit o %Programmi%\MSBuild\12.0\bin\amd64 nei sistemi operativi a 64 bit.  
  
-   I valori`ToolsVersion` sono disponibili in HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0 per i sistemi operativi a 32 bit o in HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0 per i sistemi operativi a 64 bit.  
  
-   Le proprietà `SDK35ToolsPath` e `SDK40ToolsPath` puntano a .NET Framework SDK, incluso in un pacchetto con questa versione di Visual Studio, ad esempio 8.1A per gli strumenti 4.X.  
  
## <a name="new-properties"></a>Nuove proprietà  
  
-   `MSBuildFrameworkToolsPath` è una nuova proprietà con valore %windir%\Microsoft.NET\Framework\v4.0.30319 nei sistemi operativi a 32 bit o %windir%\Microsoft.NET\Framework64\v4.0.30319 nei sistemi operativi a 64 bit. Sostituisce `MSBuildToolsPath` che può essere utilizzata per puntare agli strumenti e alle utilità di .NET Framework.  
  
-   `MSBuildToolsPath` e `MSBuildFrameworkToolsPath` presentano equivalenti a 32 bit, `MSBuildToolsPath32` e `MSBuildFrameworkToolsPath32`, che puntano sempre al percorso a 32 bit, indipendentemente dal fatto che venga utilizzato MSBuild a 32 o 64 bit.

## <a name="see-also"></a>Vedere anche
[MSBuild](msbuild.md)


