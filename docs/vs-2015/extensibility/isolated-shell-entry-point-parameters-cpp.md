---
title: Isolated Shell parametri del punto di ingresso (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6089c4ef32ef0d0b0bce081cef6d16bd569c0901
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041951"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametri del punto di ingresso Shell isolata (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando viene avviata un'applicazione basata su shell di Visual Studio, chiama il punto di ingresso di avvio della shell di Visual Studio. Le impostazioni seguenti possono essere sostituite nella chiamata al punto di ingresso di avvio della shell. Per una descrizione di ciascuna impostazione, vedere [. I file pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Il modello di Visual Studio Shell isolata consente di creare un file di origine *solutionName*cpp, dove *NomeSoluzione* è il nome della soluzione per l'applicazione. Questo file definisce il punto di ingresso principale per l'applicazione, la funzione tWinMain. Questa funzione richiama il punto di ingresso di avvio della shell.  
  
  È possibile modificare il comportamento dell'applicazione modificando queste impostazioni all'avvio dell'applicazione.  
  
## <a name="parameters"></a>Parametri  
 Il punto di ingresso di avvio della shell di Visual Studio definisce cinque parametri. Non modificare i primi quattro parametri. Il quinto parametro accetta un elenco di override delle impostazioni. Il punto di ingresso di avvio della shell viene chiamato dal punto di ingresso principale di un'applicazione.  
  
 Il punto di ingresso di avvio della shell ha la firma seguente.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Se non si desidera eseguire l'override di tutte le impostazioni dell'applicazione, lasciare il valore delle impostazioni di sostituzione parametro come un puntatore null.  
  
 Per eseguire l'override di una o più impostazioni, passare una stringa Unicode che contiene le impostazioni da sottoporre a override. La stringa è un elenco delimitato da punto e virgola di coppie nome-valore. Ogni coppia contiene il nome dell'impostazione da sostituire, seguita da un segno di uguale (=), seguito dal valore da applicare all'impostazione.  
  
> [!NOTE]
>  Non includere spazi vuoti nelle stringhe Unicode.  
  
 Per le impostazioni booleane, stringhe seguenti rappresentano il valore true; tutte le altre stringhe rappresentano il valore false. Queste stringhe sono tra maiuscole e minuscole.  
  
- \+  
  
- 1  
  
- -1  
  
- attivo  
  
- true  
  
- sì  
  
## <a name="example"></a>Esempio  
 Per disabilitare i componenti aggiuntivi e modificare il percorso di progetti predefinito per l'applicazione, è possibile impostare l'ultimo parametro da "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della Shell isolata](../extensibility/customizing-the-isolated-shell.md)   
 [File con estensione Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
