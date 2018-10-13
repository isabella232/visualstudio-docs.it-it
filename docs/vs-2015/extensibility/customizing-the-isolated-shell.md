---
title: Personalizzazione della Shell isolata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3804ded3106c68c1298063b38fb3d384685a18a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175552"
---
# <a name="customizing-the-isolated-shell"></a>Personalizzazione della Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare l'applicazione shell isolata di Visual Studio modificando i diversi aspetti dell'interfaccia utente di Visual Studio e limitando i comandi e funzionalità incluse nell'applicazione specializzata.  
  
## <a name="using-the-applicationpkgdef-file"></a>Uso di. pkgdef  
 La soluzione di modello della shell isolata include un' *SolutionName*. Application. pkgdef che consente di modificare le funzionalità seguenti:  
  
##### <a name="the-application-title"></a>Il titolo dell'applicazione  
 È possibile personalizzare il titolo dell'applicazione, ovvero il nome visualizzato nella barra del titolo dell'applicazione, modificando il valore della riga di "AppName" i *SolutionName*. . Pkgdef. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Se non si desidera il titolo dell'applicazione per visualizzare il progetto che attualmente è caricato, modificare il valore della riga di "ShowHierarchyRootInTitle" i *SolutionName*. File Application.pkgdef da dword:00000001 dword:00000000.  
  
##### <a name="the-application-icon"></a>L'icona dell'applicazione  
 È possibile personalizzare l'icona dell'applicazione, ovvero l'icona che viene visualizzato il nome dell'applicazione nella barra del titolo dell'applicazione. Copiare un'icona diversa nella directory di icona. Nelle **Esplora soluzioni**, aggiungere l'icona corrispondente nella cartella di file di risorse. Quindi aprire il file VSShellStub.rc e sostituire il valore di IDI_STUBPROGRAM con il nome della nuova icona. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Il logo della riga di comando  
 È possibile personalizzare il logo della riga di comando, ovvero il testo visualizzato quando l'applicazione viene avviata dalla riga di comando, modificando il valore della riga di "CommandLineLogo" i *SolutionName*. . Pkgdef. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Il nome della sottocartella file utente  
 È possibile modificare il nome della cartella l'applicazione mantiene informazioni per i file utente modificando il valore della riga "UserFilesSubFolderName" nella *SolutionName*. . Pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Il titolo del nodo dell'albero di soluzione nella finestra di dialogo Nuovo progetto  
 È possibile personalizzare il titolo del nodo della soluzione nella finestra di dialogo Nuovo progetto modificando il valore della riga di "NewProjDlgSlnTreeNodeTitle" i *SolutionName*. . Pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>L'intestazione di modelli installati disponibili nella finestra di dialogo Nuovo progetto  
 È possibile modificare l'intestazione di modelli installati disponibili nella finestra di dialogo Nuovo progetto modificando il valore della riga di "NewProjDlgInstalledTemplatesHdr" i *SolutionName*. . Pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Se Nascondi file esterni per impostazione predefinita  
 È possibile specificare se Nascondi file esterni per impostazione predefinita modificando il valore della riga di "HideMiscellaneousFilesByDefault" o meno il *SolutionName*. . Pkgdef. Per nascondere i file esterni, impostare il valore `dword:00000001`e per visualizzare i file, impostare il valore `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Per disabilitare la finestra di output o meno  
 È possibile specificare se disabilitare la finestra di output nell'applicazione modificando il valore della riga di "DisableOutputWindow" o meno il *SolutionName*. . Pkgdef. Per disabilitare la finestra di output, impostare il valore `dword:00000001`e per visualizzare la finestra di output, impostare il valore `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Se consentire o meno i file rilasciati nella finestra principale  
 È possibile specificare se consentire o meno file rilasciati nella finestra principale dell'applicazione modificando il valore della riga di "AllowsDroppedFilesOnMainWindow" o meno il *SolutionName*. . Pkgdef. Per consentire di file rilasciati, impostare il valore `dword:00000001`e per non consentire file rilasciati, impostare il valore `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>La pagina di ricerca predefinito  
 È possibile personalizzare la pagina del browser web, ovvero pagina visualizzata quando viene aperta la finestra del web browser, modificando il valore della riga di "DefaultSearchPage" i *SolutionName*. . Pkgdef.  
  
##### <a name="the-default-home-page"></a>La home page predefinita  
 È possibile personalizzare la home page, modificando il valore della riga di "DefaultHomePage" i *SolutionName*. . Pkgdef. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Per nascondere il concetto di soluzione o meno  
 È possibile specificare se nascondere la soluzione dell'applicazione modificando il valore della riga di "HideSolutionConcept" o meno il *SolutionName*. . Pkgdef. Per nascondere la soluzione, impostare il valore `dword:00000001`e per visualizzare la soluzione, impostare il valore `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Il motore di debug predefinito  
 È possibile modificare il motore di debug l'applicazione usa modificando il valore della riga di "DefaultDebugEngine" i *SolutionName*. File Application.pkgdef il GUID del motore di debug.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>L'estensione del file del file delle opzioni utente  
 È possibile modificare il nome della cartella l'applicazione mantiene informazioni per i file utente modificando il valore della riga "UserOptsFileExt" nella *SolutionName*. . Pkgdef.  
  
##### <a name="the-solution-file-extension"></a>L'estensione di file di soluzione  
 È possibile modificare l'estensione utilizzata per i file di soluzione, modificando il valore della riga di "SolutionFileExt" i *SolutionName*. . Pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La radice della cartella di file utente predefinito  
 È possibile modificare il nome della cartella radice del file dell'utente per l'applicazione modificando il valore della riga di "UserFilesSubFolderName" i *SolutionName*. . Pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>L'identificatore di creatore di file di soluzione  
 È possibile modificare l'identificatore usato per i file di soluzione, modificando il valore della riga di "SolutionFileCreatorIdentifier" i *SolutionName*. . Pkgdef.  
  
##### <a name="the-default-projects-location"></a>Il percorso di progetti predefinita  
 È possibile modificare il nome di percorso progetti predefinito modificando il valore della riga di "DefaultProjectsLocation" i *SolutionName*. . Pkgdef.  
  
##### <a name="the-application-localization-package"></a>Il pacchetto di localizzazione dell'applicazione  
 È possibile modificare il pacchetto di localizzazione usato per l'applicazione modificando il valore della riga di "AppLocalizationPackage" i *SolutionName*. . Pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Se mostrare la radice della gerarchia nel titolo o meno  
 È possibile specificare se visualizzare la radice della gerarchia nella barra del titolo dell'applicazione modificando il valore della riga di "ShowHierarchyRootInTitle" o meno il *SolutionName*. . Pkgdef. Per visualizzare la radice della gerarchia, impostare il valore `dword:00000001`e per nascondere la radice della gerarchia, impostare il valore `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Specifica di una pagina iniziale  
 Per specificare una pagina iniziale per l'applicazione personalizzata, nelle *SolutionName*. . Pkgdef, impostare il valore "DisableStartPage" `dword:00000000`, quindi in `[$RootKey$\StartPage\Default]` impostare l'URI per il percorso del file con estensione XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Nel file Applicationcommands.vsct il *SolutionName*dell'interfaccia utente del progetto, rimuovere i commenti per la voce "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 È necessario aggiungere il file con estensione XAML e qualsiasi file grafici è necessario, il *SolutionName* progetto. Questi file devono essere copiati in effetti per i *SolutionName* directory del progetto, non è stato aggiunta da altre directory.  
  
 In tutti i file, impostare il **tipo di elemento** proprietà **File Shell isolata** affinché i file da copiare il *$RootFolder$* directory. (Per impostare il **tipo di elemento** proprietà, il pulsante destro e selezionare **proprietà**. Questa proprietà è possibile trovare **le proprietà di configurazione**, **generali**.)  
  
 Per altre informazioni sulla personalizzazione delle pagine iniziali, vedere [personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Utilizzo di altri elementi della shell isolata  
 È possibile usare altri file e progetti inclusi nel modello di soluzione shell isolata per personalizzare ulteriormente l'applicazione.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Abilita/disabilita i pacchetti di Visual Studio  
 Il *SolutionName*file con estensione pkgundef consente di disabilitare determinati tipi di funzionalità di Visual Studio escludendo alcuni pacchetti. Ad esempio, la riga seguente:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Rimuove il progetto file esterni dal set di modelli di progetto visualizzato nei **nuovo progetto** finestra di dialogo. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Abilita/disabilita i comandi di menu  
 Il *SolutionName*UI.vsct file include un elenco di commento di tutti i comandi di menu disponibili della shell isolata. Per disabilitare un determinato comando, rimuovere il commento la riga corrispondente. Ad esempio, per disabilitare il commento/Dividi finestra, rimuovere il commento di `<Define name="No_SplitCommand"/>` riga. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>La bitmap utilizzata nella schermata iniziale  
 È possibile personalizzare la bitmap utilizzata nella schermata iniziale, ovvero la finestra che viene visualizzata quando l'applicazione viene avviata, modificando il valore della riga di "SplashScreenBitmap" i *SolutionName*. . Pkgdef. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>La Guida/informazioni sulla finestra  
 Nel modello di shell isolata c'è un progetto separato è possibile usare per personalizzare la Guida/sulla casella per l'applicazione. Per altre informazioni, vedere [procedura dettagliata: creazione di un'applicazione Shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).

