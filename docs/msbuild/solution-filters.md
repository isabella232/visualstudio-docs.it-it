---
title: Filtri della soluzione in MSBuild
description: Vengono illustrati i filtri della soluzione e viene illustrato come compilare un file di filtro della soluzione con MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 998103828d20827e8a1d99e0cc34d7f9beb6bd7c
ms.sourcegitcommit: 9179c33a78c2ac690ce908d7c73eef50b6e367f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87401030"
---
# <a name="solution-filters-in-msbuild"></a>Filtri della soluzione in MSBuild

I file di filtro della soluzione sono file JSON con estensione *slnf* che indicano quali progetti compilare o caricare da tutti i progetti in una soluzione. A partire da MSBuild 16,7, è possibile richiamare MSBuild sul file di filtro della soluzione per compilare la soluzione con l'applicazione di filtri abilitata. 

> [!NOTE]
> Il file di filtro della soluzione riduce il set di progetti che verranno caricati o compilati e semplifica il formato. Il file della soluzione è ancora necessario.

## <a name="build-a-solution-filter-from-the-command-line"></a>Compilare un filtro soluzione dalla riga di comando

La compilazione di un file di filtro della soluzione dalla riga di comando utilizza esattamente la stessa sintassi della compilazione di un file di soluzione. Specificare il file di filtro della soluzione invece della soluzione da compilare con il filtro abilitato, come indicato di seguito:

```console
msbuild [options] solutionFilterFile.slnf
```

È anche possibile aggiungere opzioni e proprietà aggiuntive come di consueto. Vedere informazioni di [riferimento sulla riga di comando di MSBuild](msbuild-command-line-reference.md). Questo comando Compila i progetti filtrati e tutti i progetti da cui dipendono. Quando si compila un filtro soluzione dalla riga di comando, MSBuild segue automaticamente le dipendenze. Compila un progetto se viene specificato nel filtro o a cui fa riferimento un progetto compilato.

## <a name="solution-filter-files"></a>File di filtro della soluzione

È possibile usare Visual Studio per lavorare con i file di filtro della soluzione. L'apertura di un filtro della soluzione in Visual Studio consente di visualizzare i progetti scaricati e i progetti caricati e offre la possibilità di caricare più progetti per selezionarli per la compilazione. È possibile caricare anche tutti i progetti da cui dipendono i progetti iniziali, ma ciò non è obbligatorio. Vedere [soluzioni filtrate](../ide/filtered-solutions.md).

Non è necessario che il filtro della soluzione si trovi nella stessa cartella della soluzione. Il percorso del file della soluzione è relativo al percorso del file di filtro della soluzione, ma i percorsi di ogni progetto sono relativi al file di soluzione stesso e devono corrispondere ai percorsi del progetto nel file di soluzione. Nell'esempio seguente viene illustrato l'utilizzo dei percorsi relativi:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Le barre rovesciate nei percorsi devono essere raddoppiate, dal momento che sono precedute da un carattere di escape.

## <a name="example"></a>Esempio

Di seguito è riportato un esempio di una soluzione filtrata in Visual Studio:

![Screenshot della soluzione filtrata in Visual Studio](media/solution-with-filter.png)

In questa soluzione, ClassLibrary1 viene usato sia da ProjectA che da ProjectB, quindi ClassLibrary1 viene elencato come riferimento al progetto.

Ecco il file di filtro della soluzione generato da Visual Studio:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

In questo esempio, quando si esegue la compilazione con il filtro abilitato (usando il comando `MSBuild [options] MyFilter.slnf` ), MSBuild compila MyApplication e ProjectA perché sono elencate in modo esplicito nel file di filtro della soluzione. Nell'ambito della compilazione di PROJECTA, MSBuild compila ClassLibrary1 perché ProjectA dipende da esso.  ProjectB non viene compilato. Questa discussione presuppone una compilazione pulita. Se i progetti sono stati compilati in precedenza, si applicano le regole usuali per ignorare i progetti che sono già aggiornati.

## <a name="see-also"></a>Vedere anche

- [Soluzioni filtrate](../ide/filtered-solutions.md)
- [Riferimenti alla riga di comando di MSBuild](msbuild-command-line-reference.md)
