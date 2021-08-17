---
title: Filtri della soluzione in MSBuild
description: Illustra i filtri della soluzione e illustra come compilare un file di filtro della soluzione con MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
monikerRange: '>= vs-2019'
ms.openlocfilehash: a080e6ba9703138d9ad8b6d272f09dd18c65ffb75a35fc2aa8cd42e90d00e172
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427515"
---
# <a name="solution-filters-in-msbuild"></a>Filtri della soluzione in MSBuild

I file di filtro della soluzione sono file JSON con estensione *slnf* che indicano quali progetti compilare o caricare da tutti i progetti in una soluzione. A partire da MSBuild 16.7, è possibile richiamare MSBuild nel file di filtro della soluzione per compilare la soluzione con il filtro abilitato. 

> [!NOTE]
> Il file di filtro della soluzione riduce il set di progetti che verranno caricati o compilati e semplifica il formato. Il file di soluzione è ancora necessario.

## <a name="build-a-solution-filter-from-the-command-line"></a>Compilare un filtro della soluzione dalla riga di comando

La compilazione di un file di filtro della soluzione dalla riga di comando usa esattamente la stessa sintassi della compilazione di un file di soluzione. Specificare il file di filtro della soluzione anziché la soluzione da compilare con il filtro abilitato, come indicato di seguito:

```console
msbuild [options] solutionFilterFile.slnf
```

È anche possibile aggiungere opzioni e proprietà aggiuntive come di consueto. Vedere [MSBuild riferimento alla riga di comando.](msbuild-command-line-reference.md) Questo comando compila i progetti filtrati e gli eventuali progetti da cui dipendono. Quando si compila un filtro della soluzione dalla riga di comando, MSBuild automaticamente le dipendenze. Compila un progetto se è specificato nel filtro o a cui fa riferimento un progetto compilato.

## <a name="solution-filter-files"></a>File di filtro della soluzione

È possibile usare Visual Studio per usare i file di filtro della soluzione. L'apertura di un filtro di soluzione Visual Studio i progetti scaricati e i progetti caricati e offre la possibilità di caricare altri progetti per selezionarli per la compilazione. È possibile caricare anche tutti i progetti da cui dipendono i progetti iniziali per la compilazione, ma questa operazione non è necessaria. Vedere [Soluzioni filtrate.](../ide/filtered-solutions.md)

Il filtro della soluzione non deve essere nella stessa cartella della soluzione. Il percorso del file di soluzione è relativo al percorso del file di filtro della soluzione, ma i percorsi di ogni progetto sono relativi al file di soluzione stesso e devono corrispondere ai percorsi del progetto nel file di soluzione. L'esempio seguente illustra l'uso di percorsi relativi:

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

Le barre rovesciate nei percorsi devono essere raddoppiate, perché sono precedute da caratteri di escape.

## <a name="example"></a>Esempio

Ecco un esempio di una soluzione filtrata in Visual Studio:

![Screenshot della soluzione filtrata in Visual Studio](media/solution-with-filter.png)

In questa soluzione ClassLibrary1 viene usato sia da ProjectA che da ProjectB e quindi ClassLibrary1 viene elencato come riferimento al progetto.

Di seguito è riportato il file di filtro della soluzione Visual Studio generato:

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

In questo esempio, quando si compila con il filtro abilitato (usando il comando ), MSBuild compila MyApplication e ProjectA perché sono elencati in modo esplicito nel file di filtro `MSBuild [options] MyFilter.slnf` della soluzione. Come parte della compilazione di ProjectA, MSBuild classlibrary1 perché ProjectA dipende da esso.  ProjectB non viene compilato. Questa discussione presuppone una compilazione pulita. Se i progetti sono stati compilati in precedenza, le regole consuete si applicano per ignorare i progetti già aggiornati.

## <a name="see-also"></a>Vedi anche

- [Soluzioni filtrate](../ide/filtered-solutions.md)
- [MSBuild della riga di comando](msbuild-command-line-reference.md)
