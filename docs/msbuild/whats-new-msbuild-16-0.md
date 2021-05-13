---
title: Novità di MSBuild 16.0 | Microsoft Docs
description: Informazioni sulle funzionalità e sulle proprietà modificate e aggiornate per MSBuild 16.0 e collegamento alle note sulla versione.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: cdfb552c53a40b6ad2f2349556396475926900be
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848253"
---
# <a name="whats-new-in-msbuild-160"></a>Novità di MSBuild 16.0

Questo articolo descrive le funzionalità e le proprietà aggiornate in MSBuild 16.0. Per le note dettagliate sulla versione, vedere [MSBuild 16.0.](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)

## <a name="changed-path"></a>Percorso modificato

 MSBuild viene installato nella *cartella \Current* in ogni versione di Visual Studio e i file eseguibili si trova nella *sottocartella \Bin.* Ad esempio, il percorso di *MSBuild.exe* installato con Visual Studio 2019 Community è *C:\Programmi (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* È anche possibile usare il modulo PowerShell seguente per individuare MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Proprietà modificate

 In conseguenza del nuovo numero di versione le proprietà seguenti di MSBuild sono state modificate.

- Il valore di `MSBuildToolsVersion` per questa versione degli strumenti è "Current". La versione dell'assembly è la stessa di Visual Studio 2017, ovvero 15.1.0.0.

- Il valore di `VisualStudioVersion` per questa versione degli strumenti è "16.0".

## <a name="change-waves"></a>Flussi di modifiche

A partire da MSBuild 16.8, è possibile scegliere in modo selettivo se rifiutare esplicitamente alcune modifiche potenzialmente dannose in MSBuild. Vedere [Modificare le onde.](change-waves.md)

## <a name="updates"></a>Aggiornamenti

MSBuild (e Visual Studio) ora fanno riferimento a .NET Framework 4.7.2. Se si desidera usare nuove funzionalità dell'API MSBuild, è necessario aggiornare anche l'assembly, ma il codice esistente continua a funzionare.

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
