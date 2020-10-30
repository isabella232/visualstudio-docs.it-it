---
title: '&apos;Novità di MSBuild 16,0 | Microsoft Docs'
description: Informazioni sulle funzionalità e sulle proprietà modificate e aggiornate per MSBuild 16,0 e sul collegamento alle note sulla versione.
ms.custom: SEO-VS-2020
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: a4e0079fa301d751962a945a0bf8348ffd3c359d
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047787"
---
# <a name="whats-new-in-msbuild-160"></a>Novità di MSBuild 16.0

Questo articolo descrive le funzionalità e le proprietà aggiornate in MSBuild 16.0. Per le note sulla versione dettagliate, vedere [ MSBuild 16,0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Percorso modificato

 MSBuild viene installato nella cartella *\Larghezza* in ogni versione di Visual Studio e i file eseguibili si trovano nella sottocartella *\bin* . Ad esempio, il percorso *MSBuild.exe* installato con la community di visual studio 2019 è *c:\Programmi (x86) \Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* è possibile usare anche il modulo di PowerShell seguente per individuare MSBuild: [vssetup. PowerShell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Proprietà modificate

 In conseguenza del nuovo numero di versione le proprietà seguenti di MSBuild sono state modificate.

- Il valore di `MSBuildToolsVersion` per questa versione degli strumenti è "Current". La versione dell'assembly è la stessa di Visual Studio 2017, ovvero 15.1.0.0.

- Il valore di `VisualStudioVersion` per questa versione degli strumenti è "16.0".

## <a name="updates"></a>Aggiornamenti

MSBuild (e Visual Studio) ora fanno riferimento a .NET Framework 4.7.2. Se si desidera usare nuove funzionalità dell'API MSBuild, è necessario aggiornare anche l'assembly, ma il codice esistente continua a funzionare.

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
