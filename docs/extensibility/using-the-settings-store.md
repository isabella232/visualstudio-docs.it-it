---
title: Utilizzo dell'Archivio impostazioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698511"
---
# <a name="using-the-settings-store"></a>Uso dell'archivio delle impostazioni
Esistono due tipi di archivi di impostazioni:

- Impostazioni di configurazione, che sono impostazioni di sola lettura di Visual Studio e VSPackage.Configuration settings, which are read-only Visual Studio and VSPackage settings. Visual Studio unisce le impostazioni di tutti i file .pkgdef noti in questo archivio.

- Impostazioni utente, ovvero impostazioni scrivibili, ad esempio quelle visualizzate nelle pagine della finestra di dialogo **Opzioni,** nelle pagine delle proprietà e in alcune altre finestre di dialogo. Le estensioni di Visual Studio possono usarle per l'archiviazione locale di piccole quantità di dati.

  In questa procedura dettagliata viene illustrato come leggere i dati dall'archivio delle impostazioni di configurazione. Vedere [Scrittura nell'archivio impostazioni utente](../extensibility/writing-to-the-user-settings-store.md) per una spiegazione su come scrivere nell'archivio impostazioni utente.

## <a name="creating-the-example-project"></a>Creazione del progetto di esempioCreating the Example Project
 In questa sezione viene illustrato come creare un progetto di estensione semplice con un comando di menu per la dimostrazione.

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che conterrà gli asset di estensione. Creare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un progetto `SettingsStoreExtension`VSIX denominato . È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** in **Visual Cè / Extensibility**.

2. Aggiungere ora un modello di elemento di comando personalizzato denominato **SettingsStoreCommand**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Custom Command** **Visual C.** Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file di comando in **SettingsStoreCommand.cs**. Per altre informazioni su come creare un comando personalizzato, vedere [Creazione di un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) di menuFor more information about how to create a custom command, see Creating an Extension with a Menu Command

## <a name="using-the-configuration-settings-store"></a>Utilizzo dell'archivio delle impostazioni di configurazione
 In questa sezione viene illustrato come rilevare e visualizzare le impostazioni di configurazione.

1. Nel file SettingsStorageCommand.cs aggiungere le direttive using seguenti:In the SettingsStorageCommand.cs file, add the following using directives:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. In `MenuItemCallback`, rimuovere il corpo del metodo e aggiungere queste righe ottenere l'archivio delle impostazioni di configurazione:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Il <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> è una classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> helper gestita tramite il servizio.

3. Ora scoprire se Windows Phone Tools sono installati. Il codice dovrebbe essere simile al seguente:The code should look like this:

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

5. Nell'istanza sperimentale scegliere Richiama **SettingsStoreCommand**dal menu **Strumenti** .

    Verrà visualizzata una finestra di messaggio che indica gli strumenti di sviluppo di **Microsoft Windows Phone:** seguito da **True** o **False**.

   Visual Studio mantiene l'archivio delle impostazioni nel Registro di sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Per utilizzare un editor del Registro di sistema per verificare le impostazioni di configurazione

1. Aprire Regedit.exe.

2. Spostarsi su HKEY_CURRENT_USER, Software, Microsoft Microsoft .NET\\Framework 14.0Exp_Config.

    > [!NOTE]
    > Assicurarsi che si sta esaminando la chiave che contiene 14.0Exp_Config\\e non 14.0_Config . Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni di configurazione sono nell'hive del Registro di sistema "14.0Exp_Config".

3. Espandere il nodo Prodotti installati. Se il messaggio nei passaggi precedenti è **Microsoft Windows Phone Developer Tools installato: True**, allora I prodotti installati devono contenere un nodo Strumenti di sviluppo di Microsoft Windows Phone. Se il messaggio è **Microsoft Windows Phone Developer Tools installato: False ,** allora I prodotti installati non devono contenere un nodo Strumenti di sviluppo di Microsoft Windows Phone.
