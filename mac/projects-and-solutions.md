---
title: Progetti e soluzioni
description: Questo documento offre una panoramica di progetti e soluzioni in Visual Studio per Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: ec62e9c0b449f5f2aed568735c2a10d1f6634eed
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820965"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Progetti e soluzioni in Visual Studio per Mac

Questo articolo offre una panoramica del *project* e *soluzione* concetti in Visual Studio per Mac.

> [!NOTE] 
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [progetti e soluzioni in Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Progetti

Quando si crea una nuova applicazione, sito Web, e così via in Visual Studio per Mac, iniziare con un progetto. Il progetto contiene tutti i file necessari (codice sorgente, immagini, file di dati, e così via) necessarie per compilare il file eseguibile, una libreria o sito Web.

Un progetto è definito da un file (ad esempio, `.csproj` per C# progetti) che contiene il xml che definisce il file e gerarchia di cartelle, percorsi di file e impostazioni specifici del progetto, ad esempio le impostazioni di compilazione.

Quando viene caricato un progetto da Visual Studio per Mac, il riquadro della soluzione Usa il file di progetto per visualizzare i file e cartelle nel progetto. Durante la compilazione, MSBuild legge le impostazioni dal file di progetto per creare il file eseguibile.

## <a name="solutions"></a>Soluzioni

Oggetto *soluzione* è un contenitore che raggruppa insieme uno o più progetti correlati. Le soluzioni sono descritte da un file di testo (estensione `.sln`) con un formato univoco; non destinato a essere modificato manualmente.

## <a name="managing-projects-in-the-solution-pad"></a>Gestione di progetti nel riquadro della soluzione

Dopo aver creato un progetto o caricato, è possibile usare il riquadro della soluzione per visualizzare e gestire il progetto o soluzione e i file contenuti all'interno. La figura seguente mostra il riquadro della soluzione con una soluzione .NET Core contenente due progetti:

![Soluzione di esempio con più progetti](media/solution-example.png)

È possibile gestire le proprietà di progetti e soluzioni facendo doppio clic sul nome del progetto o soluzione oppure facendo clic e scegliendo **opzioni**.

Per altre informazioni su queste opzioni, vedere l'articolo [Gestione delle proprietà di soluzioni e progetti](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Vedere anche

- [Soluzioni e progetti in Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
