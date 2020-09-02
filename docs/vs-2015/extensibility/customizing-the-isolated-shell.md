---
title: Personalizzazione della shell isolata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555968"
---
# <a name="customizing-the-isolated-shell"></a>Personalizzazione della shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare l'applicazione Visual Studio Isolated Shell cambiando diversi aspetti dell'interfaccia utente di Visual Studio e limitando i comandi e le funzionalità inclusi nell'applicazione specializzata.  
  
## <a name="using-the-applicationpkgdef-file"></a>Uso del file Application. pkgdef  
 La soluzione modello di shell isolata include un *SolutionName*. File Application. pkgdef che consente di modificare le funzionalità seguenti:  
  
##### <a name="the-application-title"></a>Titolo dell'applicazione  
 È possibile personalizzare il titolo dell'applicazione, ovvero il nome visualizzato nella barra del titolo dell'applicazione, modificando il valore della riga "AppName" in *SolutionName*. File Application. pkgdef. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Se non si desidera che il titolo dell'applicazione visualizzi il progetto attualmente caricato, modificare il valore della riga "ShowHierarchyRootInTitle" in *SolutionName*. File Application. pkgdef da DWORD: 00000001 a DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Icona dell'applicazione  
 È possibile personalizzare l'icona dell'applicazione, che è l'icona visualizzata dal nome dell'applicazione nella barra del titolo dell'applicazione. Copiare un'icona diversa nella directory dell'icona. In **Esplora soluzioni**aggiungere l'icona alla cartella file di risorse. Aprire quindi il file VSShellStub. RC e sostituire il valore di IDI_STUBPROGRAM con il nome della nuova icona. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Il logo della riga di comando  
 È possibile personalizzare il logo della riga di comando, ovvero il testo visualizzato quando l'applicazione viene avviata dalla riga di comando, modificando il valore della riga "CommandLineLogo" in *SolutionName*. File Application. pkgdef. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Nome della sottocartella file utente  
 È possibile modificare il nome della cartella che l'applicazione gestisce per i file utente modificando il valore della riga "UserFilesSubFolderName" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Titolo del nodo della struttura ad albero della soluzione nella finestra di dialogo nuovo progetto  
 È possibile personalizzare il titolo del nodo della soluzione nella finestra di dialogo nuovo progetto modificando il valore della riga "NewProjDlgSlnTreeNodeTitle" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Intestazione templates installata nella finestra di dialogo nuovo progetto  
 È possibile modificare l'intestazione dei modelli installati nella finestra di dialogo nuovo progetto modificando il valore della riga "NewProjDlgInstalledTemplatesHdr" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Indica se nascondere o meno i file esterni per impostazione predefinita  
 È possibile specificare se nascondere o meno i file esterni per impostazione predefinita modificando il valore della riga "HideMiscellaneousFilesByDefault" in *SolutionName*. File Application. pkgdef. Per nascondere i file esterni, impostare il valore `dword:00000001` e per visualizzare i file, impostare il valore `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Indica se disabilitare o meno la finestra di output  
 È possibile specificare se disabilitare o meno la finestra di output nell'applicazione modificando il valore della riga "DisableOutputWindow" in *SolutionName*. File Application. pkgdef. Per disabilitare la finestra output, impostare il valore `dword:00000001` e per visualizzare la finestra di output, impostare il valore `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Indica se consentire o meno i file eliminati nella finestra principale  
 È possibile specificare se consentire o meno i file eliminati nella finestra principale dell'applicazione modificando il valore della riga "AllowsDroppedFilesOnMainWindow" in *SolutionName*. File Application. pkgdef. Per consentire i file eliminati, impostare il valore `dword:00000001` e per non consentire i file eliminati, impostare il valore `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>Pagina di ricerca predefinita  
 È possibile personalizzare la pagina Web browser, ovvero la pagina visualizzata all'apertura della finestra del browser Web, modificando il valore della riga "DefaultSearchPage" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-default-home-page"></a>Il home page predefinito  
 È possibile personalizzare la home page modificando il valore della riga "DefaultHomePage" in *SolutionName*. File Application. pkgdef. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Indica se nascondere o meno il concetto di soluzione  
 È possibile specificare se nascondere o meno la soluzione nell'applicazione modificando il valore della riga "HideSolutionConcept" in *SolutionName*. File Application. pkgdef. Per nascondere la soluzione, impostare il valore `dword:00000001` e per visualizzare la soluzione, impostare il valore `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>Motore di debug predefinito  
 È possibile modificare il motore di debug usato dall'applicazione modificando il valore della riga "DefaultDebugEngine" in *SolutionName*. File Application. pkgdef al GUID del motore di debug.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Estensione di file del file di opzioni utente  
 È possibile modificare il nome della cartella che l'applicazione gestisce per i file utente modificando il valore della riga "UserOptsFileExt" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Estensione del file di soluzione  
 È possibile modificare l'estensione utilizzata per i file della soluzione modificando il valore della riga "SolutionFileExt" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Radice della cartella dei file utente predefiniti  
 È possibile modificare il nome della cartella radice dei file utente per l'applicazione modificando il valore della riga "UserFilesSubFolderName" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identificatore del creatore del file della soluzione  
 È possibile modificare l'identificatore usato per i file della soluzione modificando il valore della riga "SolutionFileCreatorIdentifier" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-default-projects-location"></a>Il percorso predefinito dei progetti  
 È possibile modificare il nome del percorso dei progetti predefinito modificando il valore della riga "DefaultProjectsLocation" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="the-application-localization-package"></a>Pacchetto di localizzazione dell'applicazione  
 È possibile modificare il pacchetto di localizzazione usato per l'applicazione modificando il valore della riga "AppLocalizationPackage" in *SolutionName*. File Application. pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Indica se visualizzare o meno la radice della gerarchia nel titolo  
 È possibile specificare se visualizzare o meno la radice della gerarchia nella barra del titolo dell'applicazione modificando il valore della riga "ShowHierarchyRootInTitle" in *SolutionName*. File Application. pkgdef. Per visualizzare la radice della gerarchia, impostare il valore `dword:00000001` e per nascondere la radice della gerarchia, impostare il valore `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Specifica di una pagina iniziale  
 Per specificare una pagina iniziale per l'applicazione personalizzata, in *SolutionName*. File Application. pkgdef, impostare il valore "DisableStartPage" su `dword:00000000` e in `[$RootKey$\StartPage\Default]` impostare l'URI sul percorso del file con estensione XAML:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Nel file ApplicationCommands. vsct nel progetto UI di *SolutionName*, impostare come commento la voce "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Per il progetto *SolutionName* , è necessario aggiungere il file con estensione XAML e gli eventuali file grafici necessari. Questi file devono essere effettivamente copiati nella directory del progetto *SolutionName* , non aggiunti da un'altra directory.  
  
 In tutti i file, impostare la proprietà **tipo di elemento** su file della **Shell isolata** affinché i file vengano copiati nella directory *$RootFolder $* . Per impostare la proprietà **tipo di elemento** , fare clic con il pulsante destro del mouse sul file e scegliere **Proprietà**. Questa proprietà è disponibile in **proprietà di configurazione**, **generale**.  
  
 Per ulteriori informazioni sulla personalizzazione delle pagine iniziali, vedere [personalizzazione della pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Uso di altri elementi della shell isolata  
 Per personalizzare ulteriormente l'applicazione, è possibile usare altri file e progetti inclusi nel modello di soluzione della shell isolata.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Abilita/Disabilita i pacchetti di Visual Studio  
 Il file *SolutionName*. pkgundef consente di disabilitare alcuni tipi di funzionalità di Visual Studio escludendo alcuni pacchetti. Ad esempio, la riga seguente:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 rimuove il progetto di file esterni dal set di modelli di progetto visualizzato nella finestra di dialogo **nuovo progetto** . Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Abilitare/disabilitare i comandi di menu  
 Il file *SolutionName*UI. vsct include un elenco di tutti i comandi di menu disponibili per la shell isolata. Per disabilitare un determinato comando, rimuovere il commento dalla riga corrispondente. Ad esempio, per disabilitare il commento Window/Split, rimuovere il commento dalla `<Define name="No_SplitCommand"/>` riga. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Bitmap utilizzata nella schermata iniziale  
 È possibile personalizzare la bitmap utilizzata nella schermata iniziale, ovvero la finestra visualizzata quando l'applicazione viene avviata, modificando il valore della riga "SplashScreenBitmap" in *SolutionName*. File Application. pkgdef. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Finestra della Guida/informazioni  
 Nel modello di shell isolata è disponibile un progetto separato che è possibile usare per personalizzare la casella Guida/informazioni per l'applicazione. Per altri dettagli, vedere [procedura dettagliata: creazione di un'applicazione shell isolata di base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
