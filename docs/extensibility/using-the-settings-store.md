---
title: Con il Store impostazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca57c279ceabd03f48ffaa564d42f7d023b39887
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434189"
---
# <a name="using-the-settings-store"></a>Uso dell'archivio delle impostazioni
Esistono due tipi di archivi di impostazioni:

- Impostazioni di configurazione, che sono impostazioni di Visual Studio e package VS di sola lettura. Visual Studio unisce le impostazioni da tutti i file con estensione pkgdef noti in questo archivio.

- Impostazioni utente, che sono impostazioni scrivibile, ad esempio quelli che vengono visualizzati nelle pagine di **opzioni** nella finestra di dialogo Pagine delle proprietà e alcune altre finestre di dialogo. Estensioni di Visual Studio possono usarle per l'archiviazione locale di piccole quantità di dati.

  Questa procedura dettagliata illustra come leggere i dati dall'archivio di impostazione di configurazione. Visualizzare [scrivendo la Store impostazioni utente](../extensibility/writing-to-the-user-settings-store.md) per una spiegazione di come scrivere nell'archivio delle impostazioni utente.

## <a name="creating-the-example-project"></a>Creazione del progetto di esempio
 Questa sezione illustra come creare un progetto di estensione semplice con un comando di menu a scopo dimostrativo.

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `SettingsStoreExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.

2. A questo punto aggiungere un modello di elemento di comando personalizzato denominato **SettingsStoreCommand**. Nel **Aggiungi nuovo elemento** finestra di dialogo passa alla **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **Name** campo nella parte inferiore della finestra, modificare il nome di file di comando da **SettingsStoreCommand.cs**. Per altre informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Con il Store le impostazioni di configurazione
 In questa sezione viene illustrato come rilevare e visualizzare le impostazioni di configurazione.

1. Nel file SettingsStorageCommand.cs, aggiungere quanto segue usando istruzioni:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. In `MenuItemCallback`, rimuovere il corpo del metodo e aggiungere l'archivio delle impostazioni di configurazione di ottenere le righe seguenti:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Il <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> è una classe helper gestita tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> servizio.

3. A questo punto è scoprire se sono installati gli strumenti di Windows Phone. Il codice dovrebbe essere simile al seguente:

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

5. Nell'istanza sperimentale, sul **degli strumenti** menu, fare clic su **SettingsStoreCommand richiamare**.

    Si dovrebbe vedere un messaggio **Microsoft Windows Phone Developer Tools:** aggiungendo **True** oppure **False**.

   Visual Studio mantiene l'archivio delle impostazioni nel Registro di sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Usare un editor del Registro di sistema per verificare le impostazioni di configurazione

1. Aprire Regedit.exe.

2. Passare a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.

    > [!NOTE]
    > Assicurarsi che si sta esaminando la chiave che contiene \14.0Exp_Config\ e non \14.0_Config\\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni di configurazione disponibili nell'hive del Registro di sistema "14.0Exp_Config".

3. Espandere il nodo \Installed Products\. Se il messaggio nei passaggi precedenti è **installata di Microsoft Windows Phone Developer Tools: True**, \Installed Products\ deve contenere un nodo di Microsoft Windows Phone Developer Tools. Se il messaggio è **installata di Microsoft Windows Phone Developer Tools: False**, quindi \Installed Products\ non deve contenere un nodo di Microsoft Windows Phone Developer Tools.