---
title: "Procedura: Compilare destinazioni specifiche all'interno di soluzioni tramite MSBuild.exe | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bfef86b8ea82077ba7fe3f753f9835c06c3380a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156657"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Procedura: compilare destinazioni specifiche all'interno di soluzioni tramite MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare MSBuild per compilare destinazioni specifiche di progetti specifici in una soluzione.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Per compilare una destinazione specifica di un progetto specifico in una soluzione  
  
1. Nella riga di comando digitare `MSBuild.exe <SolutionName>.sln`, dove `<SolutionName>` corrisponde al nome file della soluzione che contiene la destinazione che si vuole eseguire.  
  
2. Specificare la destinazione dopo l'opzione **/t** nel formato *NomeProgetto*:*NomeDestinazione*.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente esegue la destinazione `Rebuild` del progetto `NotInSlnFolder` e quindi esegue la destinazione `Clean` del progetto `InSolutionFolder`, che si trova nella cartella della soluzione `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [MSBuild](msbuild.md)  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
