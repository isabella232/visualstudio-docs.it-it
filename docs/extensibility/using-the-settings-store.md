---
title: Uso dell'archivio impostazioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9c42835e720fd3c33e53d862192e3e2863a4423
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632602"
---
# <a name="using-the-settings-store"></a>Uso dell'archivio delle impostazioni
Esistono due tipi di archivi delle impostazioni:

- Impostazioni di configurazione, ovvero le impostazioni di Visual Studio e VSPackage di sola lettura. Visual Studio unisce le impostazioni da tutti i file pkgdef noti in questo archivio.

- Impostazioni utente, che sono impostazioni scrivibili, ad esempio quelle visualizzate nelle pagine della finestra di dialogo **Opzioni** , le pagine delle proprietà e alcune altre finestre di dialogo. Le estensioni di Visual Studio possono usarle per l'archiviazione locale di piccole quantità di dati.

  In questa procedura dettagliata viene illustrato come leggere i dati dall'archivio delle impostazioni di configurazione. Per una spiegazione su come scrivere nell'archivio impostazioni utente, vedere [scrittura nell'archivio impostazioni utente](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Creazione del progetto di esempio
 In questa sezione viene illustrato come creare un semplice progetto di estensione con un comando di menu per la dimostrazione.

1. Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che conterrà gli asset di estensione. Creare un progetto VSIX [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] denominato `SettingsStoreExtension`. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** in  **C# Visual/Extensibility**.

2. A questo punto aggiungere un modello di elemento di comando personalizzato denominato **SettingsStoreCommand**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a **Visual C# /Extensibility** e selezionare **comando personalizzato**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file di comando in **SettingsStoreCommand.cs**. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Uso dell'archivio impostazioni di configurazione
 In questa sezione viene illustrato come rilevare e visualizzare le impostazioni di configurazione.

1. Nel file SettingsStorageCommand.cs aggiungere le direttive using seguenti:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. In `MenuItemCallback` rimuovere il corpo del metodo e aggiungere le righe seguenti per ottenere l'archivio delle impostazioni di configurazione:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Il <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> è una classe helper gestita sul servizio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>.

3. Verificare ora se sono installati Windows Phone Tools. Il codice dovrebbe essere simile al seguente:

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

5. Nell'istanza sperimentale, scegliere **richiama SettingsStoreCommand**dal menu **strumenti** .

    Verrà visualizzata una finestra di messaggio che informa che **Microsoft Windows Phone strumenti di sviluppo:** seguito da **true** o **false**.

   Visual Studio mantiene l'archivio delle impostazioni nel registro di sistema.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Per utilizzare un editor del registro di sistema per verificare le impostazioni di configurazione

1. Aprire regedit. exe.

2. Passare a HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts \\.

    > [!NOTE]
    > Assicurarsi di esaminare la chiave che contiene \14.0Exp_Config\ e non \14.0_Config \\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni di configurazione si trovano nell'hive del registro di sistema "14.0 Exp_Config".

3. Espandere il nodo \Installed Products \. Se il messaggio nei passaggi precedenti è **Microsoft Windows Phone strumenti di sviluppo installato: true**, i prodotti \Installed \ devono contenere un nodo microsoft Windows Phone strumenti di sviluppo. Se il messaggio è **Microsoft Windows Phone strumenti di sviluppo installato: false**, i prodotti \Installed \ non devono contenere un nodo microsoft Windows Phone strumenti di sviluppo.
