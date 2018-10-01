---
title: "Procedura: Compilare destinazioni specifiche all'interno di soluzioni tramite MSBuild.exe | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bdc5d824d802916c38ef0267dae0de85e8814e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517356"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Procedura: compilare destinazioni specifiche all'interno di soluzioni tramite MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: compilare destinazioni specifiche in soluzioni da usando MSBuild.exe](https://docs.microsoft.com/visualstudio/msbuild/how-to-build-specific-targets-in-solutions-by-using-msbuild-exe).  
  
  
È possibile usare MSBuild per compilare destinazioni specifiche di progetti specifici in una soluzione.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Per compilare una destinazione specifica di un progetto specifico in una soluzione  
  
1.  Nella riga di comando digitare `MSBuild.exe <SolutionName>.sln`, dove `<SolutionName>` corrisponde al nome file della soluzione che contiene la destinazione che si vuole eseguire.  
  
2.  Specificare la destinazione dopo l'opzione **/t** nel formato *NomeProgetto*:*NomeDestinazione*.  
  
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


