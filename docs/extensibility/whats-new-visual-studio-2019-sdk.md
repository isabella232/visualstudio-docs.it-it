---
title: Novità dell'SDK di Visual Studio 2019 Documenti Microsoft
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740408"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novità di Visual Studio 2019 SDK

Visual Studio SDK include le funzionalità nuove e aggiornate seguenti per Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Avviso estensioni caricate automaticamente in modo sincrono

Gli utenti visualizzeranno ora un avviso se una delle estensioni installate viene caricata automaticamente all'avvio. Per ulteriori informazioni sull'avviso, vedere [Estensioni con caricamento automatico in modo sincrono](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Visual Studio SDK singolo e unificato

È ora possibile ottenere tutti gli asset di Visual Studio SDK tramite un singolo pacchetto NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Miglioramenti alla registrazione dell'editore

Dalla sua creazione, Visual Studio ha supportato la registrazione dell'editor personalizzato in cui un editor può dichiarare la propria affinità per estensioni specifiche (ad esempio, xaml e RC) o che è adatto a qualsiasi estensione (con estensione. A partire da Visual Studio 2019 versione 16.1, il supporto per la registrazione dell'editor è stato ampliato.

### <a name="filenames"></a>Nomi file

Oltre a, o al posto di, la registrazione del supporto per una particolare estensione di file, un editor può registrare che supporta nomi di file specifici applicando il nuovo `ProvideEditorFilename` attributo al pacchetto dell'editor.

Ad esempio, un editor che supporta tutti `ProvideEditorExtension` i file .json applicherebbe questo attributo al relativo pacchetto:For example, an editor that supports all .json files would apply this attribute to its package:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partire dalla 16.1, se MyEditor supporta solo un paio di file `ProvideEditorFilename` .json noti, può invece applicare questi attributi al relativo pacchetto:Starting with 16.1, if MyEditor only supports a couple of well-known .json files, it can instead apply these attributes to its package:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Un editor può registrare uno o più UIContexts che rappresentano quando è abilitato. UIContexts vengono registrati applicando una o `ProvideEditorUIContextAttribute` più istanze di al pacchetto che registra l'editor.

Se un editor ha registrato UIContexts:If an editor has registered UIContexts:

- Se almeno uno dei relativi UIContexts registrati è attivo quando viene aperto un file con l'estensione specificata, l'editor viene incluso nella ricerca dell'editor.
- Se nessuno dei UIContexts registrati è attivo, l'editor non è incluso nella ricerca dell'editor.

Se un editor non registra alcun UIContexts, viene sempre incluso nell'editor cercare tale estensione.

Ad esempio, se un editor è disponibile solo quando un progetto in c'è aperto, può dichiarare questa affinità applicando un `ProvideEditorUIContext` attributo:For example, if an editor is only available when a C's project is open, it can declare this affinity by applying a attribute:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
