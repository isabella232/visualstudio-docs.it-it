---
title: Parametri del punto di ingresso della shell isolata (C++) | Microsoft Docs
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
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840072"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametri del punto di ingresso della shell isolata (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando un'applicazione basata su Visual Studio Shell viene avviata, chiama il punto di ingresso iniziale della shell di Visual Studio. È possibile eseguire l'override delle impostazioni seguenti nella chiamata al punto di ingresso iniziale della shell. Per una descrizione di ogni impostazione, vedere [. File pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
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
  
  Il modello di isolamento della shell di Visual Studio crea un file di origine, *SolutionName*. cpp, dove *SolutionName* è il nome della soluzione per l'applicazione. Questo file definisce il punto di ingresso principale per l'applicazione, la funzione _tWinMain. Questa funzione richiama il punto di ingresso iniziale della shell.  
  
  È possibile modificare il comportamento dell'applicazione modificando queste impostazioni all'avvio dell'applicazione.  
  
## <a name="parameters"></a>Parametri  
 Il punto di ingresso iniziale della shell di Visual Studio definisce cinque parametri. Non modificare i primi quattro parametri. Il quinto parametro accetta un elenco di override delle impostazioni. Il punto di ingresso iniziale della shell viene chiamato dal punto di ingresso principale di un'applicazione.  
  
 Il punto di ingresso iniziale della shell ha la firma seguente.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Se non si desidera eseguire l'override delle impostazioni dell'applicazione, lasciare il valore del parametro di override delle impostazioni come puntatore null.  
  
 Per eseguire l'override di una o più impostazioni, passare una stringa Unicode che contiene le impostazioni di cui eseguire l'override. La stringa è un elenco delimitato da punti e virgola di coppie nome-valore. Ogni coppia contiene il nome dell'impostazione di cui eseguire l'override, seguito da un segno di uguale (=), seguito dal valore da applicare all'impostazione.  
  
> [!NOTE]
> Non includere spazi vuoti nelle stringhe Unicode.  
  
 Per le impostazioni booleane, le stringhe seguenti rappresentano il valore true; tutte le altre stringhe rappresentano il valore false. Queste stringhe non fanno distinzione tra maiuscole e minuscole.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- sì  
  
## <a name="example"></a>Esempio  
 Per disabilitare i componenti aggiuntivi e modificare il percorso dei progetti predefiniti per l'applicazione, è possibile impostare l'ultimo parametro su "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione della shell isolata](../extensibility/customizing-the-isolated-shell.md)   
 [File con estensione Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
