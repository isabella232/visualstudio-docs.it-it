---
title: Strumenti per il rilevamento e la gestione di istanze di Visual Studio
titleSuffix: ''
description: Informazioni sugli strumenti che è possibile usare per rilevare e gestire le installazioni di Visual Studio nei computer client.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 914449fe1db792614af1f9ed22464cb9fdb91481
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306891"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Strumenti per il rilevamento e la gestione di istanze di Visual Studio

Esistono diversi strumenti che è possibile usare per rilevare Visual Studio installazioni nei computer client e per gestire le installazioni.

## <a name="detecting-existing-visual-studio-instances"></a>Rilevamento di istanze di Visual Studio esistenti

Gli strumenti e le utilità seguenti consentono di rilevare e gestire le istanze Visual Studio nei computer client:

* [**vswhere:**](https://github.com/microsoft/vswhere)eseguibile incorporato Visual Studio o disponibile per una distribuzione separata che consente di trovare il percorso di tutte le istanze Visual Studio in un computer specifico.
* [**VSSetup.PowerShell:**](https://github.com/microsoft/vssetup.powershell)script di PowerShell che usano l'API configurazione di installazione per identificare le istanze installate Visual Studio.
* [**VS-Setup-Samples:**](https://github.com/microsoft/vs-setup-samples)esempi di C# e C++ che illustrano come usare l'API di configurazione del programma di installazione per eseguire query su un'installazione esistente.
* [**Strumentazione gestione Windows (WMI):**](/windows/win32/wmisdk/wmi-start-page)Visual Studio le informazioni sull'istanza possono essere Visual Studio classe MSFT_VSInstance.
* [**L'API Configurazione di**](<xref:Microsoft.VisualStudio.Setup.Configuration>) installazione fornisce interfacce per gli sviluppatori che vogliono compilare le proprie utilità per l'Visual Studio istanze.
* [**Microsoft Endpoint Configuration Manager inventario software:**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory)può essere usato per raccogliere informazioni sulle istanze Visual Studio nei dispositivi client.

## <a name="using-vswhereexe"></a>Uso di vswhere.exe

`vswhere.exe` viene incluso automaticamente in Visual Studio 2017 e versioni successive oppure è possibile scaricarlo dalla pagina delle versioni [vswhere](https://github.com/Microsoft/vswhere/releases). Usare `vswhere -?` per ottenere informazioni sullo strumento. Ad esempio, questo comando mostra tutte le versioni di Visual Studio, incluse le versioni precedenti del prodotto e le versioni non definitive, e restituisce i risultati in formato JSON:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Uso Strumentazione gestione Windows (WMI)

Se l'Visual Studio Client Detector Utility è installata nel computer, è possibile eseguire una query per Visual Studio informazioni sull'istanza tramite WMI. L'utilità di rilevamento client Visual Studio viene installata per impostazione predefinita ogni Visual Studio 2017, Visual Studio 2019 e Visual Studio 2022 che è stato rilasciato il 12 maggio 2020 o dopo. È anche disponibile nel catalogo [Microsoft Update se](https://catalog.update.microsoft.com/) si vuole installarlo in modo indipendente.  Per un esempio di come usare l'utilità per restituire Visual Studio informazioni sull'istanza, aprire PowerShell come amministratore nel computer client e digitare il comando seguente:

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Uso di Microsoft Endpoint Configuration Manager

[Microsoft Endpoint Configuration Manager funzionalità di inventario software](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) possono essere usate per eseguire query e raccogliere informazioni sulle istanze Visual Studio nei dispositivi client. Ad esempio, la query seguente restituirà il nome visualizzato, la versione e il nome del dispositivo in cui è installato Visual Studio per tutte le istanze di Visual Studio 2017 e 2019 installate:

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
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

1. Dal menu principale regedit selezionare **File** Load Hive... e quindi selezionare il file del Registro di sistema privato, archiviato  >   nella **cartella AppData\Local.** Ad esempio:

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` corrisponde all'istanza di Visual Studio che si vuole trovare.

Verrà chiesto di fornire un nome di hive, che diventerà il nome dell'hive isolato. Al termine dell'operazione sarà possibile trovare il Registro di sistema nell'hive isolato appena creato.

> [!IMPORTANT]
> Prima di avviare nuovamente Visual Studio, è necessario scaricare l'hive isolato appena creato. A tale scopo, selezionare **Scarica**  >  **hive dal** menu principale Regedit. (Se non si esegue questa operazione, il file rimarrà bloccato e non sarà possibile avviare Visual Studio).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
