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
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b6b641081c9b969cadd2c9517967adb8cc4cb1e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547440"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Strumenti per il rilevamento e la gestione di istanze di Visual Studio

Sono disponibili diversi strumenti che è possibile usare per rilevare le installazioni di Visual Studio nei computer client e per gestire le installazioni.

## <a name="detecting-existing-visual-studio-instances"></a>Rilevamento di istanze di Visual Studio esistenti

Gli strumenti e le utilità seguenti consentono di rilevare e gestire le istanze installate di Visual Studio nei computer client:

* [**vswhere**](https://github.com/microsoft/vswhere): un eseguibile incorporato in Visual Studio o disponibile per la distribuzione separata che consente di trovare la posizione di tutte le istanze di Visual Studio in un computer specifico.
* [**VSSetup. PowerShell**](https://github.com/microsoft/vssetup.powershell): script di PowerShell che usano l'API di configurazione del programma di installazione per identificare le istanze installate di Visual Studio.
* [**Vs-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): esempi di C# e C++ che illustrano come usare l'API di configurazione del programma di installazione per eseguire una query su un'installazione esistente.
* [**Strumentazione gestione Windows (WMI)**](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page): le informazioni sull'istanza di Visual Studio possono essere sottoposte a query tramite la classe MSFT_VSInstance di Visual Studio. 
* L' [**API di configurazione dell'installazione**](<xref:Microsoft.VisualStudio.Setup.Configuration>) fornisce le interfacce per gli sviluppatori che desiderano creare utilità personalizzate per interrogare le istanze di Visual Studio.
* [**Microsoft Endpoint Configuration Manager inventario software**](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): può essere usato per raccogliere informazioni sulle istanze di Visual Studio nei dispositivi client. 

## <a name="using-vswhereexe"></a>Uso di vswhere.exe

`vswhere.exe` viene automaticamente incluso in Visual Studio 2017 e versioni successive oppure è possibile scaricarlo dalla [pagina delle versioni di vswhere](https://github.com/Microsoft/vswhere/releases). Usare `vswhere -?` per ottenere informazioni sullo strumento. Ad esempio, questo comando Mostra tutte le versioni di Visual Studio, incluse le versioni precedenti del prodotto e le versioni preliminari, e restituisce i risultati in formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Utilizzo di Strumentazione gestione Windows (WMI)

Se l'utilità rilevamento client di Visual Studio è installata nel computer, è possibile eseguire una query per le informazioni sull'istanza di Visual Studio tramite WMI. L'utilità rilevamento client di Visual Studio viene installata per impostazione predefinita con tutti gli aggiornamenti di Visual Studio 2017 e Visual Studio 2019 rilasciati il 12 maggio 2020. È inoltre disponibile nel [catalogo Microsoft Update](https://catalog.update.microsoft.com/) se si desidera installarlo in modo indipendente.  Per un esempio di come usare l'utilità per restituire le informazioni sull'istanza di Visual Studio, aprire PowerShell come amministratore nel computer client e digitare il comando seguente:

```cmd
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Utilizzo di Microsoft endpoint Configuration Manager 

[Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) le funzionalità di inventario software possono essere usate per eseguire query e raccogliere informazioni sulle istanze di Visual Studio nei dispositivi client. Ad esempio, la query seguente restituirà il nome visualizzato, la versione e il nome del dispositivo su cui è installato Visual Studio per tutte le istanze di Visual Studio 2017 e 2019 installate: 

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

1. Dal menu principale di Regedit selezionare **file**  >  **Load hive...** e quindi selezionare il file del registro di sistema privato, memorizzato nella cartella **AppData\Local.** Ad esempio:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` corrisponde all'istanza di Visual Studio che si vuole trovare.

Verrà chiesto di fornire un nome di hive, che diventerà il nome dell'hive isolato. Al termine dell'operazione sarà possibile trovare il Registro di sistema nell'hive isolato appena creato.

> [!IMPORTANT]
> Prima di avviare nuovamente Visual Studio, è necessario scaricare l'hive isolato appena creato. A tale scopo, selezionare **file**  >  **unload hive** dal menu principale di Regedit. (Se non si esegue questa operazione, il file rimarrà bloccato e non sarà possibile avviare Visual Studio).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Guida di Visual Studio Administrator](../install/visual-studio-administrator-guide.md)
