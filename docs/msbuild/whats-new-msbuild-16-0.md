---
title: '&apos;Novità di MSBuild 16,0 | Microsoft Docs'
description: Informazioni sulle funzionalità e sulle proprietà modificate e aggiornate per MSBuild 16,0 e sul collegamento alle note sulla versione.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 24b106442456f8bfbd415c4559cba71e463418d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933791"
---
# <a name="whats-new-in-msbuild-160"></a>Novità di MSBuild 16.0

Questo articolo descrive le funzionalità e le proprietà aggiornate in MSBuild 16.0. Per le note sulla versione dettagliate, vedere [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Percorso modificato

 MSBuild viene installato nella cartella *\Larghezza* in ogni versione di Visual Studio e i file eseguibili si trovano nella sottocartella *\bin* . Ad esempio, il percorso *MSBuild.exe* installato con la community di visual studio 2019 è *c:\Programmi (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* è possibile usare anche il modulo di PowerShell seguente per individuare MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Proprietà modificate

 In conseguenza del nuovo numero di versione le proprietà seguenti di MSBuild sono state modificate.

- Il valore di `MSBuildToolsVersion` per questa versione degli strumenti è "Current". La versione dell'assembly è la stessa di Visual Studio 2017, ovvero 15.1.0.0.

- Il valore di `VisualStudioVersion` per questa versione degli strumenti è "16.0".

## <a name="change-waves"></a>Flussi di modifiche

A partire da MSBuild 16,8, è possibile scegliere in modo selettivo se rifiutare esplicitamente determinate modifiche potenzialmente dannose in MSBuild. Vedere [Change Waves](change-waves.md).

## <a name="updates"></a>Aggiornamenti

MSBuild (e Visual Studio) ora fanno riferimento a .NET Framework 4.7.2. Se si desidera usare nuove funzionalità dell'API MSBuild, è necessario aggiornare anche l'assembly, ma il codice esistente continua a funzionare.

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
