---
title: Uso di più processori per la compilazione di progetti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631302"
---
# <a name="use-multiple-processors-to-build-projects"></a>Usare più processori per la compilazione di progetti

MSBuild è in grado di trarre vantaggio dai sistemi che dispongono di più processori o di più componenti principali. Per ogni processore disponibile viene creato un processo di compilazione separato. Se, ad esempio, nel sistema sono presenti quattro processori, vengono creati quattro diversi processi di compilazione. MSBuild è in grado di elaborare queste compilazioni simultaneamente e pertanto il tempo di compilazione complessivo è ridotto. Tuttavia, la compilazione parallela introduce alcune modifiche ai processi di compilazione. Questo argomento descrive queste modifiche.

## <a name="project-to-project-references"></a>Riferimenti da progetto a progetto

 Quando il Microsoft Build Engine rileva un riferimento da progetto a progetto (P2P) mentre usa compilazioni parallele per compilare un progetto, compila il riferimento solo una volta. Se due progetti presentano lo stesso riferimento P2P, questo non viene ricompilato per ogni progetto. Il motore di compilazione restituisce invece lo stesso riferimento P2P a entrambi i progetti dipendenti. Eventuali richieste successive nella sessione per la stessa destinazione offriranno lo stesso riferimento P2P.

## <a name="cycle-detection"></a>Rilevamento del ciclo

 Il rilevamento del ciclo funziona come in MSBuild 2,0, con la differenza che ora MSBuild può segnalare il rilevamento del ciclo in un momento diverso o nella compilazione.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Errori ed eccezioni durante le compilazioni parallele

 Nelle compilazioni parallele possono verificarsi errori ed eccezioni in momenti diversi rispetto a quanto avviene nelle compilazioni non parallele e, se un progetto non viene compilato, gli altri processi di compilazione di progetti proseguono normalmente. MSBuild non interromperà la compilazione di progetti in parallelo con quella che ha avuto esito negativo. La compilazione degli altri progetti continua finché non viene completata correttamente o non si verifica un errore. Tuttavia, se <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> è stato abilitato, nessuna compilazione verrà arrestata anche se si verifica un errore.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++file di progetto (. vcxproj) e di soluzione (. sln)

 Entrambi C++ i file di progetto ( *. vcxproj*) e di soluzione ( *. sln*) possono essere passati all' [attività MSBuild](../msbuild/msbuild-task.md). Per C++ i progetti, viene chiamato viene VCWrapperProject, quindi viene creato il progetto MSBuild interno. Per C++ le soluzioni, viene creato un SolutionWrapperProject, quindi viene creato il progetto MSBuild interno. In entrambi i casi, il progetto risultante viene considerato come qualsiasi altro progetto MSBuild.

## <a name="multi-process-execution"></a>Esecuzione di più processi

 Quasi tutte le attività correlate alla compilazione richiedono che la directory corrente rimanga costante durante l'intero processo di compilazione per evitare errori di percorso. Di conseguenza, i progetti non possono essere eseguiti in thread diversi in MSBuild perché causano la creazione di più directory.

 Per evitare questo problema ma abilitare ancora le compilazioni multiprocessore, MSBuild utilizza "isolamento processo". Utilizzando l'isolamento dei processi, MSBuild può creare un massimo di `n` processi, in cui `n` è uguale al numero di processori disponibili nel sistema. Se, ad esempio, MSBuild compila una soluzione in un sistema che dispone di due processori, vengono creati solo due processi di compilazione. Questi processi vengono poi riusati per compilare tutti i progetti nella soluzione.

## <a name="see-also"></a>Vedere anche

- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Attività](../msbuild/msbuild-tasks.md)
