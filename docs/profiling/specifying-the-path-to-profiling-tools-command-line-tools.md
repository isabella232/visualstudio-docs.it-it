---
title: Specifica del percorso degli strumenti da riga di comando di profilatura
description: Specificare il percorso degli strumenti da riga di comando degli strumenti di profilatura quando il percorso Strumenti di profilatura strumenti da riga di comando non viene aggiunto alla variabile di ambiente PATH.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d96ea6d373f01210e7226e809c01c216506c86c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157254"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Specificare il percorso degli strumenti da riga di comando degli strumenti di profilatura

Il percorso degli strumenti da riga di comando di Strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è aggiunto alla variabile di ambiente PATH. Nei computer a 32 bit gli strumenti si trovano in un'unica directory. Nei computer a 64 bit sono disponibili versioni a 32 bit e a 64 bit degli strumenti di profilatura.

## <a name="32-bit-computers"></a>Computer a 32 bit

Per il codice nativo, le API del profiler di Visual Studio si trovano in *VSPerf.dll*. Il file di intestazione *VSPerf.h* e la libreria di importazione *VSPerf.lib* si trovano nella directory *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.

 Per il codice gestito, le API del profiler siMicrosoft.VisualStudio.Profiler.dll *.* Questa DLL è disponibile nella directory *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

## <a name="64-bit-computers"></a>Computer a 64 bit

Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione da sottoporre a profilatura.

- La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:

     (nativo) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*
     
     (gestito) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:

     (nativo) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*

     (gestito) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
