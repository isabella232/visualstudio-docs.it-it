---
title: Novità di Visual Studio 2019 SDK | Microsoft Docs
description: L Visual Studio SDK offre le funzionalità nuove e aggiornate per Visual Studio 2019, inclusi i miglioramenti della registrazione dell'editor.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3ca803eb330f0640910e271ec5bf531de0ccdf58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028396"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novità di Visual Studio 2019 SDK

L Visual Studio SDK include le funzionalità nuove e aggiornate seguenti per Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Avviso relativo alle estensioni caricate automaticamente in modo sincrono

Gli utenti ora visualizzano un avviso se una delle estensioni installate viene caricata automaticamente in modo sincrono all'avvio. Per altre informazioni sull'avviso, vedere [Estensioni caricate automaticamente](synchronously-autoloaded-extensions.md)in modo sincrono.

## <a name="single-unified-visual-studio-sdk"></a>SDK singolo e Visual Studio unificato

È ora possibile ottenere tutti gli asset Visual Studio SDK tramite un singolo pacchetto NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Miglioramenti della registrazione dell'editor

Dopo la creazione, Visual Studio ha supportato la registrazione dell'editor personalizzato in cui un editor può dichiarare la propria affinità per estensioni specifiche (ad esempio, .xaml e .rc) o che è adatto per qualsiasi estensione (.*). A partire Visual Studio 2019 versione 16.1, si amplia il supporto per la registrazione dell'editor.

### <a name="filenames"></a>Nomi file

Oltre a o invece di registrare il supporto per una determinata estensione di file, un editor può registrare che supporta nomi di file specifici applicando il nuovo attributo al `ProvideEditorFilename` pacchetto dell'editor.

Ad esempio, un editor che supporta tutti i file JSON applica questo `ProvideEditorExtension` attributo al pacchetto:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partire dalla versione 16.1, se MyEditor supporta solo un paio di file JSON noti, può invece applicare questi attributi `ProvideEditorFilename` al pacchetto:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UiContexts

Un editor può registrare uno o più UIContext che rappresentano quando è abilitato. Gli UIContext vengono registrati applicando una o più istanze `ProvideEditorUIContextAttribute` di al pacchetto che registra l'editor.

Se un editor ha registrato UIContexts:

- Se almeno uno dei relativi UIContext registrati è attivo quando viene aperto un file con l'estensione specificata, l'editor viene incluso nella ricerca nell'editor.
- Se nessuno degli UIContext registrati è attivo, l'editor non viene incluso nella ricerca nell'editor.

Se un editor non registra uiContext, viene sempre incluso nella ricerca dell'estensione nell'editor.

Ad esempio, se un editor è disponibile solo quando un progetto C# è aperto, può dichiarare questa affinità applicando un `ProvideEditorUIContext` attributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
