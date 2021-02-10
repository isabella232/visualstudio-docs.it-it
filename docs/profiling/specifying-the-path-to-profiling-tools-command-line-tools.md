---
title: Specifica del percorso degli strumenti da riga di comando per la profilatura
description: Specificare il percorso degli strumenti da riga di comando disponibili negli strumenti di profilatura quando il percorso degli strumenti da riga di comando Strumenti di profilatura non viene aggiunto alla variabile di ambiente PATH.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7b53b37f670bf6bf8cc579fd6897ba344135a9e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949948"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Specificare il percorso degli strumenti da riga di comando degli strumenti di profilatura

Il percorso degli strumenti da riga di comando di Strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è aggiunto alla variabile di ambiente PATH. Nei computer a 32 bit gli strumenti si trovano in un'unica directory. Nei computer a 64 bit sono disponibili versioni a 32 bit e a 64 bit degli strumenti di profilatura.

## <a name="32-bit-computers"></a>Computer a 32 bit

Per il codice nativo, le API del profiler di Visual Studio si trovano in *VSPerf.dll*. Il file di intestazione *VSPerf.h* e la libreria di importazione *VSPerf.lib* si trovano nella directory *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.

 Per il codice gestito, le API del profiler si trovano nel *Microsoft.VisualStudio.Profiler.dll*. Questa DLL è disponibile nella directory *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

## <a name="64-bit-computers"></a>Computer a 64 bit

Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione da sottoporre a profilatura.

- La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:

     Native *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK.*
     
     gestito *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:

     Native *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     gestito *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
