---
title: Novità di MSBuild 15 | Microsoft Docs
description: Vedere le funzionalità modificate, aggiornate e nuove di MSBuild 15, disponibili per il .NET Core SDK e per la compilazione di progetti .NET Core in Windows, macOS e Linux.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: bcf84506f44e6aab30e0d5ce10e19f05a4a87c09
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132028"
---
# <a name="whats-new-in-msbuild-15"></a>Novità di MSBuild 15

MSBuild è ora incluso in [.NET Core SDK](https://www.microsoft.com/net/download/core) e consente di compilare progetti .NET Core in Windows, macOS e Linux.

## <a name="changed-path"></a>Percorso modificato

 MSBuild viene ora installato in una cartella in ogni versione di Visual Studio. Ad esempio, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. Per individuare MSBuild, è anche possibile usare il modulo di PowerShell [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild non viene più installato nella Global Assembly Cache. Per fare riferimento a MSBuild a livello di codice, usare i pacchetti NuGet. Per altre informazioni, vedere [Aggiornamento di un'applicazione esistente per MSBuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Proprietà modificate

 In conseguenza del nuovo numero di versione le proprietà seguenti di MSBuild sono state modificate.

- Il valore di `MSBuildToolsVersion` per questa versione degli strumenti è 15.0. La versione dell'assembly è la 15.1.0.0.

- Il percorso di `MSBuildToolsPath` non è più fisso. Per impostazione predefinita, si trova nella cartella *MSBuild\15.0\Bin* relativa al percorso di installazione di Visual Studio, ma il percorso di installazione di Visual Studio può essere modificato in fase di installazione.

- I valori di `ToolsVersion` non vengono più impostato nel Registro di sistema.

- Le proprietà `SDK35ToolsPath` e `SDK40ToolsPath` puntano a .NET Framework SDK, incluso in un pacchetto con questa versione di Visual Studio, ad esempio 10.0A per gli strumenti 4.X.

## <a name="updates"></a>Aggiornamenti

- [Project elemento](../msbuild/project-element-msbuild.md) ha un nuovo `SDK` attributo . L'attributo `Xmlns` è ora facoltativo. Per altre informazioni sull'attributo `SDK`, vedere [Procedura: Usare SDK di progetto MSBuild](../msbuild/how-to-use-project-sdk.md), [Pacchetti, metapacchetti e framework](/dotnet/core/packages) e [Aggiunte al formato csproj per .NET Core](/dotnet/core/tools/csproj).
- [L'elemento Item](../msbuild/item-element-msbuild.md) all'esterno delle destinazioni ha un nuovo `Update` attributo . È stata inoltre eliminata la restrizione relativa all'attributo `Remove`.
- *Directory.Build.props* è un file definito dall'utente che fornisce personalizzazioni ai progetti in una directory. Questo file viene importato automaticamente da *Microsoft.Common.props,* a meno che la proprietà `ImportDirectoryBuildTargets` non sia impostata su **false.** *Directory.Build.targets* viene importato da *Microsoft.Common.targets*.
- Eventuali metadati il cui nome non è in conflitto con l'elenco di attributi corrente possono essere espressi come un attributo. Per altre informazioni, vedere [Elemento Item.](../msbuild/item-element-msbuild.md)

## <a name="new-property-functions"></a>Nuove funzioni di proprietà

- `EnsureTrailingSlash` aggiunge una barra finale a un percorso se non ne esiste già una.
- `NormalizePath` combina gli elementi del percorso e assicura che la stringa di output includa i caratteri di separatore di directory corretti per il sistema operativo corrente.
- `NormalizeDirectory` combina gli elementi del percorso, aggiunge una barra finale e assicura che la stringa di output includa i caratteri di separatore di directory corretti per il sistema operativo corrente.
- `GetPathOfFileAbove` restituisce il percorso del file che precede quello corrente. Dal punto di vista funzionale equivale a una chiamata a `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`.

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
