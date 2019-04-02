---
title: Novità in Visual Studio 2019 SDK | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: daa4203ccdcbce89f1eb09efdd9433210bcbc987
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2019
ms.locfileid: "58856645"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Novità in Visual Studio 2019 SDK

Visual Studio SDK ha le seguenti funzionalità nuove e aggiornate per Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>In modo sincrono le estensioni caricate automaticamente avviso

Gli utenti ora visualizzeranno un messaggio di avviso se eventuali estensioni installate in modo sincrono vengono caricate automaticamente all'avvio. Altre informazioni sull'avviso nella [in modo sincrono le estensioni caricate automaticamente](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Singola e unificata Visual Studio SDK

È ora possibile ottenere tutte le risorse di Visual Studio SDK tramite un singolo pacchetto NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Miglioramenti della registrazione di editor

Dopo la creazione, Visual Studio ha supportato la registrazione di editor personalizzato in cui un editor può dichiarare relativa affinità per estensioni specifiche (ad esempio, con estensione XAML e RC) o che è adatto a qualsiasi estensione (. *). A partire da Visual Studio 2019 versione 16.1, abbiamo ampliare il supporto per la registrazione di editor.

### <a name="filenames"></a>Nomi file

In aggiunta, o al posto di registrazione del supporto per un'estensione di file specifico, un editor può registrare che supporta i nomi di file specifico applicando il nuovo `ProvideEditorFilename` attributo al pacchetto dell'editor.

Ad esempio, un editor che supporta tutti i file con estensione JSON verrà applicata questa `ProvideEditorExtension` dell'attributo relativo pacchetto:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

A partire da 16.1, se MyEditor supporta solo un paio di file con estensione JSON ben noti, può invece applicare questi `ProvideEditorFilename` attributi per il pacchetto:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Contesti dell'interfaccia utente

Un editor è possibile registrare uno o più contesti dell'interfaccia utente che rappresentano quando è abilitato. Contesti dell'interfaccia utente vengono registrati tramite l'applicazione di uno o più istanze di `ProvideEditorUIContextAttribute` al pacchetto che si registra l'editor.

Se un editor ha registrato contesti dell'interfaccia utente:

- Se almeno uno dei relativi registrati contesti dell'interfaccia utente è attivo quando viene aperto un file con estensione specificata, l'editor è incluso nella ricerca dell'editor.
- Se nessuno dei contesti dell'interfaccia utente registrato è attivo, l'editor non è incluso nella ricerca dell'editor.

Se un editor non registra alcun contesti dell'interfaccia utente, viene sempre incluso nella ricerca dell'editor per l'estensione.

Se, ad esempio, un editor è disponibile solo quando un C# progetto è aperto, è possibile dichiarare questo affinità applicando una `ProvideEditorUIContext` attributo:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```