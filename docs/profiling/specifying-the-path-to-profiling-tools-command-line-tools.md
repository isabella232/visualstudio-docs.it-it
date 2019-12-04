---
title: Specifica del percorso degli strumenti da riga di comando degli strumenti di profilatura | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 087407f511c038a369694beca8a9fe4ecc2ff7b7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771577"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Specificare il percorso degli strumenti da riga di comando degli strumenti di profilatura

Il percorso degli strumenti da riga di comando di Strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è aggiunto alla variabile di ambiente PATH. Nei computer a 32 bit gli strumenti si trovano in un'unica directory. Nei computer a 64 bit sono disponibili versioni a 32 bit e a 64 bit degli strumenti di profilatura.

## <a name="32-bit-computers"></a>Computer a 32 bit

::: moniker range="vs-2017"
 Per il codice nativo, le API del profiler di Visual Studio si trovano in *VSPerf.dll*. Il file di intestazione *VSPerf.h* e la libreria di importazione *VSPerf.lib* si trovano nella directory *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK*.
::: moniker-end

 Per il codice gestito, le API del profiler si trovano in *Microsoft.VisualStudio.Profiler.dll*. Questa DLL è disponibile nella directory *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*.

## <a name="64-bit-computers"></a>Computer a 64 bit

Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione da sottoporre a profilatura.

::: moniker range="vs-2017"
- La directory predefinita per gli strumenti di profilatura per applicazioni a 32 bit è la seguente:

     (nativa) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* (gestita) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- La directory predefinita per gli strumenti di profilatura per applicazioni a 64 bit è la seguente:

     (nativa) *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK* (gestita) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
::: moniker-end
