---
title: Parametri del punto di ingresso (C++) Shell isolata | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 78993e12c1ab4098e20aad243faaa487ff0ea35b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametri del punto di ingresso Shell isolata (C++)
Quando si avvia un'applicazione basata su shell di Visual Studio, chiama il punto di ingresso di avvio di shell di Visual Studio. Le impostazioni seguenti possono essere sostituite nella chiamata al punto di ingresso di avvio della shell. Per una descrizione di ogni impostazione, vedere [. File pkgdef](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   AppName  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Il modello di Visual Studio Shell Isolated crea un file di origine, *solutionName*. cpp, in cui *solutionName* è il nome della soluzione per l'applicazione. Questo file definisce il punto di ingresso principale per l'applicazione, la funzione tWinMain. Questa funzione richiama il punto di ingresso di avvio della shell.  
  
 È possibile modificare il comportamento dell'applicazione mediante la modifica di queste impostazioni all'avvio dell'applicazione.  
  
## <a name="parameters"></a>Parametri  
 Il punto di ingresso di avvio di shell di Visual Studio definisce cinque parametri. Non modificare i primi quattro parametri. Il quinto parametro accetta un elenco di override delle impostazioni. Il punto di ingresso di avvio della shell viene chiamato dal punto di ingresso principale di un'applicazione.  
  
 Il punto di ingresso di avvio della shell ha la firma seguente.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Se non si desidera eseguire l'override di tutte le impostazioni dell'applicazione, lasciare il valore delle impostazioni di sostituire il parametro come un puntatore null.  
  
 Per eseguire l'override di una o più impostazioni, passare una stringa Unicode che contiene le impostazioni da sottoporre a override. La stringa è un elenco delimitato da punto e virgola di coppie nome-valore. Ogni coppia contiene il nome dell'impostazione per eseguire l'override, seguito da un segno di uguale (=), seguito dal valore da applicare all'impostazione.  
  
> [!NOTE]
>  Non includere spazi vuoti nelle stringhe Unicode.  
  
 Per le impostazioni booleane, le stringhe seguenti rappresentano il valore true; tutte le altre stringhe rappresentano il valore false. Queste stringhe sono tra maiuscole e minuscole.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   attivo  
  
-   true  
  
-   sì  
  
## <a name="example"></a>Esempio  
 Per disabilitare i componenti aggiuntivi e modificare il percorso di progetti predefinito per l'applicazione, è possibile impostare il parametro ultimo "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione Shell isolata](customizing-the-isolated-shell.md)   
 [. File pkgdef](modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)