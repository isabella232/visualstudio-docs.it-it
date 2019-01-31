---
title: Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 209c2263e35bc4e6c5bfffb03b4a760e8cc15a45
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791752"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il percorso degli strumenti da riga di comando di Strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] non è aggiunto alla variabile di ambiente PATH. Nei computer a 32 bit gli strumenti si trovano in un'unica directory. Nei computer a 64 bit sono disponibili versioni a 32 bit e a 64 bit degli strumenti di profilatura.  
  
## <a name="32-bit-computers"></a>Computer a 32 bit  
 Nei computer a 32 bit la directory predefinita per gli strumenti di profilatura è *Unità*\Programmi\Microsoft Visual Studio 11.0\Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Computer a 64 bit  
 Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione da sottoporre a profilatura.  
  
-   La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:  
  
     *Unità*\Programmi (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools  
  
-   La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:  
  
     *Unità*\Programmi (x86)\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\x64
