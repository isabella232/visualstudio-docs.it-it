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
ms.openlocfilehash: 7fadcff84c4b927a7718d7d4ad1311918ae0f18a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199784"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il percorso degli strumenti da riga di comando di Strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] non è aggiunto alla variabile di ambiente PATH. Nei computer a 32 bit gli strumenti si trovano in un'unica directory. Nei computer a 64 bit sono disponibili versioni a 32 bit e a 64 bit degli strumenti di profilatura.  
  
## <a name="32-bit-computers"></a>Computer a 32 bit  
 Nei computer a 32 bit la directory predefinita degli strumenti del profiler è *unità*\Programmi\microsoft Visual Studio 11.0 \ Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Computer a 64 bit  
 Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione da sottoporre a profilatura.  
  
- La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:  
  
     *Unità*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools  
  
- La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:  
  
     *Unità*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools\x64
