---
title: Strumenti per il rilevamento e la gestione di istanze di Visual Studio
titleSuffix: ''
description: Informazioni sugli strumenti che è possibile usare per rilevare e gestire le installazioni di Visual Studio nei computer client.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6a72f78e89af41509711c94a00c8ab11b11fc549
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018220"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Strumenti per il rilevamento e la gestione di istanze di Visual Studio

Sono disponibili diversi strumenti che è possibile usare per rilevare le installazioni di Visual Studio nei computer client e anche per gestire le installazione.

## <a name="detecting-existing-visual-studio-instances"></a>Rilevamento di istanze di Visual Studio esistenti

Sono stati resi disponibili diversi strumenti che consentono di rilevare e gestire le istanze installate di Visual Studio nei computer client:

* [vswhere](https://github.com/microsoft/vswhere): file eseguibile incorporato in Visual Studio o disponibile per una distribuzione separata che consente di trovare il percorso di tutte le istanze di Visual Studio in un computer specifico.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): script PowerShell che usano l'API di configurazione del programma di installazione per identificare le istanze di Visual Studio installate.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): esempi C# e C++ che illustrano come usare l'API di configurazione del programma di installazione per eseguire query su un'installazione esistente.

L'[API di configurazione del programma di installazione](<xref:Microsoft.VisualStudio.Setup.Configuration>) include inoltre interfacce per gli sviluppatori che intendono creare utilità personalizzate per eseguire interrogazioni sulle istanze di Visual Studio.

## <a name="using-vswhereexe"></a>Uso di vswhere.exe

`vswhere.exe` viene automaticamente incluso in Visual Studio (a partire da Visual Studio 2017 versione 15.2 e versioni successive) oppure è possibile scaricarlo dalla [pagina delle versioni di vswhere](https://github.com/Microsoft/vswhere/releases). Usare `vswhere -?` per ottenere informazioni sullo strumento. Ad esempio, questo comando visualizza tutte le versioni di Visual Studio, incluse le versioni precedenti del prodotto e le versioni non definitive e restituisce i risultati in formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```
::: moniker range="vs-2017"

> [!TIP]
> Per altre informazioni sull'installazione di Visual Studio 2017, vedere l'[archivio degli articoli sulla configurazione di Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Modifica del Registro di sistema per un'istanza di Visual Studio

In Visual Studio le impostazioni del Registro di sistema vengono archiviate in un percorso privato, che consente la presenza nello stesso computer di più istanze side-by-side della stessa versione di Visual Studio.

Questi elementi non vengono archiviati nel Registro di sistema globale ed è quindi necessario seguire istruzioni speciali per usare l'editor del Registro di sistema per apportare modifiche alle impostazioni del registro:

1. Se si ha un'istanza di Visual Studio aperta, chiuderla.

1. Avviare `regedit.exe`.

1. Selezionare il nodo `HKEY_LOCAL_MACHINE`.

1. Nel menu principale di Regedit selezionare **File** > **Carica hive** e quindi selezionare il file di registro privato archiviato nella cartella **AppData\Local**. Ad esempio:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` corrisponde all'istanza di Visual Studio che si vuole trovare.

Verrà chiesto di fornire un nome di hive, che diventerà il nome dell'hive isolato. Al termine dell'operazione sarà possibile trovare il Registro di sistema nell'hive isolato appena creato.

> [!IMPORTANT]
> Prima di avviare nuovamente Visual Studio, è necessario scaricare l'hive isolato appena creato. A questo scopo, nel menu principale di Regedit selezionare **File** > **Scarica hive**. (Se non si esegue questa operazione, il file rimarrà bloccato e non sarà possibile avviare Visual Studio).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
