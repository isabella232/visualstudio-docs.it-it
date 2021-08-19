---
title: Uso di più processori per la compilazione di progetti | Microsoft Docs
description: Informazioni su MSBuild i vantaggi dei sistemi con più processori o core creando un processo di compilazione separato per ogni processore disponibile.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 814db4514454659780021c17e873a8e2363cb54f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142442"
---
# <a name="use-multiple-processors-to-build-projects"></a>Usare più processori per la compilazione di progetti

MSBuild è in grado di trarre vantaggio dai sistemi che dispongono di più processori o di più componenti principali. Per ogni processore disponibile viene creato un processo di compilazione separato. Se, ad esempio, nel sistema sono presenti quattro processori, vengono creati quattro diversi processi di compilazione. MSBuild possibile elaborare queste compilazioni contemporaneamente e pertanto il tempo di compilazione complessivo è ridotto. Tuttavia, la compilazione parallela introduce alcune modifiche ai processi di compilazione. Questo argomento descrive queste modifiche.

## <a name="project-to-project-references"></a>Riferimenti da progetto a progetto

 Quando il Microsoft Build Engine rileva un riferimento da progetto a progetto (P2P) mentre usa compilazioni parallele per compilare un progetto, compila il riferimento una sola volta. Se due progetti presentano lo stesso riferimento P2P, questo non viene ricompilato per ogni progetto. Il motore di compilazione restituisce invece lo stesso riferimento P2P a entrambi i progetti dipendenti. Eventuali richieste successive nella sessione per la stessa destinazione offriranno lo stesso riferimento P2P.

## <a name="cycle-detection"></a>Rilevamento del ciclo

 Il rilevamento del ciclo funziona come in MSBuild 2.0, ad eccezione del fatto che ora MSBuild può segnalare il rilevamento del ciclo in un momento diverso o nella compilazione.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Errori ed eccezioni durante le compilazioni parallele

 Nelle compilazioni parallele possono verificarsi errori ed eccezioni in momenti diversi rispetto a quanto avviene nelle compilazioni non parallele e, se un progetto non viene compilato, gli altri processi di compilazione di progetti proseguono normalmente. MSBuild non arresterà la compilazione del progetto che viene compilata in parallelo con quella che ha avuto esito negativo. La compilazione degli altri progetti continua finché non viene completata correttamente o non si verifica un errore. Tuttavia, se <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> è stato abilitato, nessuna compilazione verrà arrestata anche se si verifica un errore.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>File di progetto C++ (con estensione vcxproj) e di soluzione (con estensione sln)

 Sia i progetti C++ [(con](../msbuild/msbuild-task.md)estensione *vcxproj*) che i file della soluzione ( con estensione *sln*) possono essere passati all MSBuild attività . Per i progetti C++, viene chiamato VCWrapperProject e quindi viene creato MSBuild progetto interno. Per le soluzioni C++, viene creato un progetto SolutionWrapperProject, quindi viene creato il MSBuild interno. In entrambi i casi, il progetto risultante viene considerato come qualsiasi altro MSBuild progetto.

## <a name="multi-process-execution"></a>Esecuzione di più processi

 Quasi tutte le attività correlate alla compilazione richiedono che la directory corrente rimanga costante durante l'intero processo di compilazione per evitare errori di percorso. Di conseguenza, i progetti non possono essere eseguiti in thread diversi MSBuild perché causerebbero la creazione di più directory.

 Per evitare questo problema, ma abilitare comunque compilazioni multiprocessore, MSBuild usa l'isolamento dei processi. Usando l'isolamento dei MSBuild è possibile creare un massimo di processi, dove è uguale al numero di `n` `n` processori disponibili nel sistema. Ad esempio, se MSBuild compila una soluzione in un sistema con due processori, vengono creati solo due processi di compilazione. Questi processi vengono poi riusati per compilare tutti i progetti nella soluzione.

## <a name="see-also"></a>Vedi anche

- [Compilare più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Attività](../msbuild/msbuild-tasks.md)
