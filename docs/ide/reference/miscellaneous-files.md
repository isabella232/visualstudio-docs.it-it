---
title: File esterni
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3787ce7cd6c7355c86b6e6ef077311c603265fc1
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461432"
---
# <a name="miscellaneous-files"></a>File esterni

Può essere necessario usare l'editor di Visual Studio per usare file indipendentemente da un progetto o una soluzione. Mentre si ha una soluzione aperta, è possibile aprire e modificare i file senza aggiungerli a una soluzione o a un progetto. I file che si intende usare in modo indipendente sono denominati file esterni. I file esterni sono esterni a soluzioni e progetti, non sono inclusi nelle compilazioni e non possono essere inclusi in una soluzione sotto il controllo del codice sorgente.

L'apertura di file in modo indipendente da un progetto o una soluzione è utile per diversi motivi. Si potrebbe voler visualizzare un file durante lo sviluppo di una soluzione basata su un progetto, ma che non è parte integrante dello sviluppo della soluzione. Tra gli esempi comuni vi sono note o istruzioni di sviluppo, lo schema del database e segmenti di codice. L'utente potrebbe anche voler creare un file autonomo.

![Progetti di soluzioni](../../ide/reference/media/projects_solutions_misc.gif)

Esplora soluzioni può visualizzare una cartella **File esterni** per i file se sono abilitate le opzioni per la cartella. È possibile impostare le opzioni da [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md). Dopo la chiusura di un file esterno, esso non è associato ad alcuna soluzione o progetto particolare a meno che non sia stata abilitata un'opzione a tale scopo.

La cartella **File esterni** rappresenta i file come collegamenti. Sebbene questa cartella non faccia parte di una soluzione, all'apertura di una soluzione vengono aperti di nuovo alcuni o tutti i file esterni aperti quando la soluzione è stata chiusa l'ultima volta, in base alle impostazioni per la cartella.

> [!NOTE]
> Alcuni dei file che non vengono visualizzati nella cartella **File esterni** sono file che non è possibile modificare nell'IDE, ad esempio file ZIP e DOC. L'IDE non rileva i file che possono essere modificati solo tramite un editor esterno.

## <a name="commands-available-in-the-ide"></a>Comandi disponibili nell'IDE

I menu, le barre degli strumenti e i comandi in essi contenuti cambiano a seconda del formato del file aperto. Quando si apre un file di testo, ad esempio, si apre la barra degli strumenti dell'editor di testo e sono disponibili i relativi comandi. Se in seguito si apre un file XML Schema, viene visualizzata la barra degli strumenti XML Schema. Mentre si modifica l'XML Schema, i comandi della barra degli strumenti dell'editor di testo o la stessa barra degli strumenti non sono disponibili. L'XML Schema è la finestra attiva e di conseguenza ha il contesto della selezione corrente. Quando si passa da un file di progetto a un file esterno non vengono più visualizzati tutti i comandi correlati al progetto ma soltanto quelli direttamente correlati al file esterno.

## <a name="folder-display-options"></a>Opzioni di visualizzazione della cartella

È possibile impostare le opzioni di visualizzazione per la cartella **File esterni** in modo che venga visualizzata anche se non è aperto alcun file esterno. Il file della soluzione non gestisce in modo permanente un elenco di file esterni. Usa una funzionalità facoltativa che permette di memorizzare l'elenco dei file usati di recente (ultimi elementi usati) per ogni utente.

## <a name="see-also"></a>Vedere anche

- [Sviluppare codice in Visual Studio senza progetti o soluzioni](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)
- [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md)