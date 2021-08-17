---
title: Progetti e soluzioni
description: Questo documento offre una panoramica di progetti e soluzioni in Visual Studio per Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 67bb49027e268f272e93fb80de6004a756b8695040450ad4b0d1c2b86912ca29
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121438555"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Progetti e soluzioni in Visual Studio per Mac

Questo articolo presenta una panoramica dei concetti di *progetto* e *soluzione* in Visual Studio per Mac.

> [!NOTE] 
> Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Progetti e soluzioni in Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Progetti

Quando si crea una nuova applicazione, un nuovo sito Web e così via in Visual Studio per Mac, si inizia configurando un progetto. Nel progetto sono inclusi tutti i file (codice sorgente, immagini, file di dati e così via) necessari per compilare il file eseguibile, la libreria o il sito Web.

Un progetto è definito da un file (ad esempio, `.csproj` per i progetti C#) in cui è incluso il codice XML che definisce la gerarchia di file e cartelle, i percorsi dei file e le impostazioni specifiche del progetto, ad esempio le impostazioni di compilazione.

Quando un progetto viene caricato da Visual Studio per Mac, la finestra della soluzione usa il file di progetto per visualizzare i file e le cartelle nel progetto. Durante la compilazione, MSBuild legge le impostazioni dal file di progetto per creare il file eseguibile.

## <a name="solutions"></a>Soluzioni

Una *soluzione* è un contenitore che raggruppa uno o più progetti correlati. Le soluzioni sono descritte da un file di testo (con estensione `.sln`) in un formato univoco, per il quale non è prevista la modifica manuale.

## <a name="managing-projects-in-the-solution-window"></a>Gestione di progetti nella finestra della soluzione

Dopo aver creato o caricato un progetto, è possibile usare la finestra della soluzione per visualizzare e gestire il progetto o la soluzione e i file contenuti all'interno di . La figura seguente mostra la finestra della soluzione con una soluzione .NET Core che contiene due progetti:

![Soluzione di esempio con più progetti](media/solution-example.png)

È possibile gestire le proprietà di progetti e soluzioni facendo doppio clic sul nome corrispondente oppure facendo clic con il pulsante destro del mouse e scegliendo **Opzioni**.

Per altre informazioni su queste opzioni, vedere l'articolo [Gestione delle proprietà di soluzioni e progetti](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Vedi anche

- [Soluzioni e progetti in Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
