---
title: Personalizzazione Shell isolata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9f5a6059d36493c93ceae249879530e49182acf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-isolated-shell"></a>Personalizzazione Shell isolata
Modificando i vari aspetti dell'interfaccia utente di Visual Studio e limitando i comandi e le funzionalità incluse in un'applicazione specializzata, è possibile personalizzare l'applicazione di Visual Studio isolated shell.  
  
## <a name="using-the-applicationpkgdef-file"></a>Utilizzo di pkgdef  
 La soluzione di modello della shell isolata include un *SolutionName*. Application. pkgdef che consente di modificare le funzionalità seguenti:  
  
##### <a name="the-application-title"></a>Il titolo dell'applicazione  
 È possibile personalizzare il titolo dell'applicazione, ovvero il nome visualizzato nella barra del titolo dell'applicazione, modificando il valore della riga di "AppName" il *SolutionName*. . Pkgdef. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Se si desidera il titolo dell'applicazione per visualizzare il progetto che è attualmente caricato, modificare il valore della riga di "ShowHierarchyRootInTitle" il *SolutionName*. File di Application.pkgdef da DWORD: 00000001 a DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Icona dell'applicazione  
 È possibile personalizzare l'icona dell'applicazione, ovvero l'icona visualizzata dal nome dell'applicazione nella barra del titolo dell'applicazione. Copiare un'icona diversa nella directory di icona. In **Esplora**, aggiungere l'icona di cartella dei file di risorse. Quindi aprire il file VSShellStub.rc e sostituire il valore di IDI_STUBPROGRAM con il nome della nuova icona. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Il logo della riga di comando  
 È possibile personalizzare il logo della riga di comando, ovvero il testo che viene visualizzato quando l'applicazione viene avviata dalla riga di comando, modificando il valore della riga di "CommandLineLogo" il *SolutionName*. . Pkgdef. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Il nome della sottocartella file utente  
 È possibile modificare il nome della cartella di cui l'applicazione mantiene informazioni per i file utente modificando il valore della riga di "UserFilesSubFolderName" *SolutionName*. . Pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Il titolo del nodo dell'albero di soluzione nella finestra di dialogo Nuovo progetto  
 È possibile personalizzare il titolo del nodo della soluzione nella finestra di dialogo Nuovo progetto modificando il valore della riga di "NewProjDlgSlnTreeNodeTitle" il *SolutionName*. . Pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>L'intestazione modelli installati nella finestra di dialogo Nuovo progetto  
 È possibile modificare l'intestazione modelli installati nella finestra di dialogo Nuovo progetto modificando il valore della riga di "NewProjDlgInstalledTemplatesHdr" il *SolutionName*. . Pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Se si desidera file esterni nascosti per impostazione predefinita  
 È possibile specificare di file esterni nascosti per impostazione predefinita per la modifica del valore della riga di "HideMiscellaneousFilesByDefault" o meno il *SolutionName*. . Pkgdef. Per nascondere i file esterni, impostare il valore `dword:00000001`e per visualizzare i file, impostare il valore `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Se si desidera disabilitare la finestra di output  
 È possibile specificare se disabilitare la finestra di output nell'applicazione modificando il valore della riga di "DisableOutputWindow" o meno il *SolutionName*. . Pkgdef. Per disabilitare la finestra di output, impostare il valore `dword:00000001`e per visualizzare la finestra di output, impostare il valore `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Se i file rilasciati nella finestra principale di consentire o meno  
 È possibile specificare se consentire file rilasciati nella finestra principale dell'applicazione modificando il valore della riga di "AllowsDroppedFilesOnMainWindow" o meno il *SolutionName*. . Pkgdef. Per consentire i file rilasciati, impostare il valore `dword:00000001`e per disabilitare il file rilasciati, impostare il valore `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Pagina di ricerca predefinita  
 È possibile personalizzare la pagina web browser, pagina che viene visualizzato quando viene aperta la finestra del web browser, modificando il valore della riga di "DefaultSearchPage" il *SolutionName*. . Pkgdef.  
  
##### <a name="the-default-home-page"></a>La home page predefinita  
 È possibile personalizzare la home page, modificando il valore della riga di "DefaultHomePage" il *SolutionName*. . Pkgdef. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Se si desidera nascondere il concetto di soluzione  
 È possibile specificare se nascondere la soluzione dell'applicazione modificando il valore della riga di "HideSolutionConcept" o meno il *SolutionName*. . Pkgdef. Per nascondere la soluzione, impostare il valore `dword:00000001`e per visualizzare la soluzione, impostare il valore `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Il motore di debug predefinito  
 È possibile modificare l'applicazione usa modificando il valore della riga di "DefaultDebugEngine" il motore di debug di *SolutionName*. File Application.pkgdef al GUID del motore di debug.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>L'estensione del file di opzioni utente  
 È possibile modificare il nome della cartella di cui l'applicazione mantiene informazioni per i file utente modificando il valore della riga di "UserOptsFileExt" *SolutionName*. . Pkgdef.  
  
##### <a name="the-solution-file-extension"></a>L'estensione di file di soluzione  
 È possibile modificare l'estensione utilizzata per i file di soluzione modificando il valore della riga di "SolutionFileExt" il *SolutionName*. . Pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La radice della cartella di file utente predefinito  
 È possibile modificare il nome della cartella radice del file utente per l'applicazione modificando il valore della riga di "UserFilesSubFolderName" il *SolutionName*. . Pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identificatore creatore del file di soluzione  
 È possibile modificare l'identificatore utilizzato per i file di soluzione modificando il valore della riga di "SolutionFileCreatorIdentifier" il *SolutionName*. . Pkgdef.  
  
##### <a name="the-default-projects-location"></a>La posizione di progetti predefinita  
 È possibile modificare il nome di percorso progetti predefinito modificando il valore della riga di "DefaultProjectsLocation" il *SolutionName*. . Pkgdef.  
  
##### <a name="the-application-localization-package"></a>Il pacchetto di localizzazione dell'applicazione  
 È possibile modificare il pacchetto di localizzazione utilizzato per l'applicazione modificando il valore della riga di "AppLocalizationPackage" il *SolutionName*. . Pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Se mostrare la radice della gerarchia nel titolo o meno  
 È possibile specificare se visualizzare o meno per la radice della gerarchia nella barra del titolo dell'applicazione modificando il valore della riga di "ShowHierarchyRootInTitle" il *SolutionName*. . Pkgdef. Per mostrare la radice della gerarchia, impostare il valore `dword:00000001`e per nascondere la radice della gerarchia, impostare il valore `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Specifica una pagina iniziale  
 Per specificare una pagina iniziale per l'applicazione personalizzata, nel *SolutionName*. . Pkgdef, impostare il valore "DisableStartPage" `dword:00000000`e in `[$RootKey$\StartPage\Default]` impostare l'URI per il percorso del file con estensione XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Nel file Applicationcommands.vsct il *SolutionName*dell'interfaccia utente del progetto, impostare come commento la voce "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 È necessario aggiungere il file XAML e qualsiasi file di grafica, è necessario, al *SolutionName* progetto. Questi file devono effettivamente essere copiati i *SolutionName* directory del progetto, non è stato aggiunta da altre directory.  
  
 In tutti i file, impostare il **tipo di elemento** proprietà **File Shell isolata** in ordine per i file da copiare il *$RootFolder$* directory. (Per impostare il **tipo di elemento** proprietà, il pulsante destro e selezionare **proprietà**. Questa proprietà è disponibile in **le proprietà di configurazione**, **generale**.)  
  
 Per ulteriori informazioni sulla personalizzazione delle pagine di avvio, vedere [personalizzazione della pagina iniziale](../../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Utilizzo di altri elementi della shell isolata  
 È possibile utilizzare altri file e progetti inclusi nel modello di soluzione shell isolata per personalizzare ulteriormente l'applicazione.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Abilitare o disabilitare i pacchetti di Visual Studio  
 Il *SolutionName*.pkgundef file consente di disabilitare alcuni tipi di funzionalità di Visual Studio escludendo alcuni pacchetti. Ad esempio, la riga seguente:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Rimuove il progetto file esterni dal set di modelli di progetto visualizzati di **nuovo progetto** finestra di dialogo. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Abilitare o disabilitare i comandi di menu  
 Il *SolutionName*UI.vsct file include un elenco di commento di tutti i comandi di menu disponibili per la shell isolata. Per disabilitare un comando specifico, rimuovere il commento la riga corrispondente. Ad esempio, per disabilitare il commento/suddivisione della finestra, rimuovere il commento di `<Define name="No_SplitCommand"/>` riga. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Mappa di bit utilizzata nella schermata iniziale  
 È possibile personalizzare la mappa di bit utilizzata nella schermata iniziale, ovvero la finestra che viene visualizzata quando l'applicazione viene avviata, modificando il valore della riga di "SplashScreenBitmap" il *SolutionName*. . Pkgdef. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>La Guida/informazioni sulla finestra  
 Nel modello di shell isolata è un progetto separato, è possibile utilizzare per personalizzare la Guida/informazioni su una casella per l'applicazione. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](walkthrough-creating-a-basic-isolated-shell-application.md).