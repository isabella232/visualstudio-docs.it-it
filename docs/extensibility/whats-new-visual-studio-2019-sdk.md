---
title: Novità di Visual Studio 2019 SDK | Microsoft Docs
description: Visual Studio SDK le funzionalità nuove e aggiornate per Visual Studio 2019, inclusi i miglioramenti apportati alla registrazione dell'editor.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c05e6fccf3b45c8ab6fa1386c848d6ee33094e2d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877611"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novità di Visual Studio 2019 SDK

Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Avviso di estensioni autocaricate in modo sincrono

Gli utenti visualizzeranno un avviso se una delle estensioni installate viene caricata in modo sincrono all'avvio. Per altre informazioni sull'avviso, vedere [estensioni autocaricate in modo sincrono](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Singolo Visual Studio SDK unificato

È ora possibile ottenere tutti gli asset di Visual Studio SDK tramite un singolo pacchetto NuGet [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Miglioramenti della registrazione dell'editor

Dal momento della creazione, Visual Studio ha supportato la registrazione dell'editor personalizzato, in cui un editor può dichiarare l'affinità per estensioni specifiche (ad esempio, XAML e RC) oppure è adatto per qualsiasi estensione (*). A partire da Visual Studio 2019 versione 16,1, viene ampliato il supporto per la registrazione dell'editor.

### <a name="filenames"></a>Nomi file

Oltre alla registrazione del supporto per una particolare estensione di file o al posto di, è possibile registrare un editor che supporta nomi di file specifici applicando il nuovo `ProvideEditorFilename` attributo al pacchetto dell'editor.

Ad esempio, un editor che supporta tutti i file con estensione JSON applica questo `ProvideEditorExtension` attributo al pacchetto:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partire da 16,1, se un editor supporta solo un paio di file con estensione JSON noti, può invece applicare questi `ProvideEditorFilename` attributi al pacchetto:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Un editor può registrare uno o più UIContexts che rappresentano quando è abilitato. UIContexts vengono registrate applicando una o più istanze di `ProvideEditorUIContextAttribute` al pacchetto che registra l'editor.

Se un editor ha registrato UIContexts:

- Se almeno uno dei UIContexts registrati è attivo quando viene aperto un file con l'estensione specificata, l'editor viene incluso nella ricerca dell'editor.
- Se nessuno dei UIContexts registrati è attivo, l'editor non è incluso nella ricerca dell'editor.

Se un editor non registra alcun UIContexts, viene sempre incluso nella ricerca dell'estensione dell'editor.

Ad esempio, se un editor è disponibile solo quando un progetto C# è aperto, può dichiarare questa affinità applicando un `ProvideEditorUIContext` attributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
