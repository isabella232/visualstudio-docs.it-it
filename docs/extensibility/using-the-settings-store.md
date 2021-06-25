---
title: Uso dell'archivio impostazioni | Microsoft Docs
description: Informazioni su come leggere i dati dall'archivio delle impostazioni di configurazione, che sono impostazioni di sola Visual Studio e VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d7fff5bc3eeeb3b4515e2e47027f5b88fb7807d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898383"
---
# <a name="using-the-settings-store"></a>Uso dell'archivio delle impostazioni
Esistono due tipi di archivi di impostazioni:

- Impostazioni di configurazione, che sono impostazioni di sola Visual Studio e VSPackage. Visual Studio unisce le impostazioni di tutti i file con estensione pkgdef noti in questo archivio.

- Impostazioni utente, ovvero impostazioni scrivibili, ad esempio quelle  visualizzate nelle pagine della finestra di dialogo Opzioni , nelle pagine delle proprietà e in alcune altre finestre di dialogo. Visual Studio estensioni possono usarle per l'archiviazione locale di piccole quantità di dati.

  Questa procedura dettagliata illustra come leggere i dati dall'archivio delle impostazioni di configurazione. Per una spiegazione su come scrivere [nell'archivio delle impostazioni](../extensibility/writing-to-the-user-settings-store.md) utente, vedere Scrittura nell'archivio delle impostazioni utente.

## <a name="creating-the-example-project"></a>Creazione del progetto di esempio
 Questa sezione illustra come creare un progetto di estensione semplice con un comando di menu a scopo dimostrativo.

1. Ogni Visual Studio'estensione inizia con un progetto di distribuzione VSIX che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `SettingsStoreExtension` . È possibile trovare il modello di progetto VSIX nella **finestra di dialogo Nuovo** progetto in Visual **C# /Extensibility.**

2. Aggiungere ora un modello di elemento di comando personalizzato **denominato SettingsStoreCommand.** Nella finestra **di dialogo Aggiungi nuovo** elemento passare a Visual **C# /Extensibility** e selezionare **Comando personalizzato.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in **SettingsStoreCommand.cs**. Per altre informazioni su come creare un comando personalizzato, vedere Creazione [di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Uso dell'archivio delle impostazioni di configurazione
 Questa sezione illustra come rilevare e visualizzare le impostazioni di configurazione.

1. Nel file SettingsStorageCommand.cs aggiungere le direttive using seguenti:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. In rimuovere il corpo del metodo e aggiungere queste righe per ottenere `MenuItemCallback` l'archivio delle impostazioni di configurazione:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    è <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> una classe helper gestita sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> servizio.

3. A questo punto, verificare se Windows Phone Strumenti di distribuzione sono installati. Il codice dovrebbe essere simile al seguente:

   ```
   private void MenuItemCallback(object sender, EventArgs e)
   {
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;
       MessageBox.Show(message);
   }
   ```

4. Testare il codice. Compilare il progetto e avviare il debug.

5. Nell'istanza sperimentale scegliere **Richiama** impostazioniStoreCommand dal menu **Strumenti.**

    Verrà visualizzata una finestra di messaggio che indica **Microsoft Windows Phone Strumenti di sviluppo:** seguito da **True** o **False.**

   Visual Studio mantiene l'archivio delle impostazioni nel Registro di sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Per usare un editor del Registro di sistema per verificare le impostazioni di configurazione

1. Aprire Regedit.exe.

2. Passare a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Assicurarsi di cercare la chiave che contiene \14.0Exp_Config\ e non \14.0_Config \\ . Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni di configurazione si verificano nell'hive del Registro di sistema "14.0Exp_Config".

3. Espandere il nodo \Prodotti installati\. Se il messaggio nei passaggi precedenti è **Microsoft Windows Phone Strumenti di sviluppo Installed: True**, \Installed Products\ deve contenere un nodo microsoft Windows Phone Strumenti di sviluppo. Se il messaggio è **Microsoft Windows Phone Strumenti di sviluppo Installed: False**, \Installed Products\ non deve contenere un nodo microsoft Windows Phone Strumenti di sviluppo.
