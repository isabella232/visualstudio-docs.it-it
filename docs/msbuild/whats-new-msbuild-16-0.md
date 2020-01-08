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
ms.openlocfilehash: 3e6ecfc1c08f30eb0232f230d955967d95bc32ee
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566969"
---
# <a name="whats-new-in-msbuild-160"></a>Novità di MSBuild 16.0

Questo articolo descrive le funzionalità e le proprietà aggiornate in MSBuild 16.0. Per le note sulla versione dettagliate (solo bozza), vedere [MSBuild 16.0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

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
