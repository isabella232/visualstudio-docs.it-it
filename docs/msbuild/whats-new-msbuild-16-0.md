---
title: Novità di MSBuild 16.0 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 1a83ce4cf47f8a1607e562dfdb69b5b7374de1a6
ms.sourcegitcommit: ca9375d1c48355f2e9f7bc1b2d3f0e94eb15db00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022341"
---
# <a name="whats-new-in-msbuild-160"></a>Novità di MSBuild 16.0

Questo articolo descrive le funzionalità e le proprietà aggiornate in MSBuild 16.0. Per le note sulla versione dettagliate, vedere [MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Percorso modificato

 MSBuild viene installato nella cartella *\Current* in ogni versione di Visual Studio. Ad esempio, *C:\Programmi (x86)\Microsoft Visual Studio\Current\Enterprise\MSBuild*. Per individuare MSBuild, è anche possibile usare il modulo di PowerShell [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Proprietà modificate

 In conseguenza del nuovo numero di versione le proprietà seguenti di MSBuild sono state modificate.

- Il valore di `MSBuildToolsVersion` per questa versione degli strumenti è "Current". La versione dell'assembly è la stessa di Visual Studio 2017, ovvero 15.1.0.0.

- Il valore di `VisualStudioVersion` per questa versione degli strumenti è "16.0".

## <a name="updates"></a>Aggiornamenti

MSBuild (e Visual Studio) ora fanno riferimento a .NET Framework 4.7.2. Se si desidera usare nuove funzionalità dell'API MSBuild, è necessario aggiornare anche l'assembly, ma il codice esistente continua a funzionare.

## <a name="see-also"></a>Vedere anche
- [MSBuild](../msbuild/msbuild.md)
