---
title: File esterni
description: Informazioni su come usare i file non inclusi in un progetto o in una soluzione di Visual Studio.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc797fe7676d24a80867cc318cbe02f94e90e7d0
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561097"
---
# <a name="miscellaneous-files"></a>File esterni

Può essere necessario usare l'editor di Visual Studio per usare file indipendentemente da un progetto o una soluzione. Mentre si ha una soluzione aperta, è possibile aprire e modificare i file senza aggiungerli a una soluzione o a un progetto. I file che si intende usare in modo indipendente sono denominati file esterni. I file esterni sono esterni a soluzioni e progetti, non sono inclusi nelle compilazioni e non possono essere inclusi in una soluzione sotto il controllo del codice sorgente.

L'apertura di file in modo indipendente da un progetto o una soluzione è utile per diversi motivi. Si potrebbe voler visualizzare un file durante lo sviluppo di una soluzione basata su un progetto, ma che non è parte integrante dello sviluppo della soluzione. Tra gli esempi comuni vi sono note o istruzioni di sviluppo, lo schema del database e segmenti di codice. L'utente potrebbe anche voler creare un file autonomo.

![Progetti di soluzioni](../../ide/reference/media/projects_solutions_misc.gif)

Esplora soluzioni possibile visualizzare una cartella di **file esterni** per i file se sono abilitate le opzioni per la cartella. È possibile impostare le opzioni da [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md). Dopo la chiusura di un file esterno, esso non è associato ad alcuna soluzione o progetto particolare a meno che non sia stata abilitata un'opzione a tale scopo.

La cartella **file esterni** rappresenta i file come collegamenti. Sebbene questa cartella non faccia parte di una soluzione, all'apertura di una soluzione vengono aperti di nuovo alcuni o tutti i file esterni aperti quando la soluzione è stata chiusa l'ultima volta, in base alle impostazioni per la cartella.

> [!NOTE]
> Alcuni dei file che non vengono visualizzati nella cartella **file esterni** sono file che non è possibile modificare all'interno dell'IDE, ad esempio i file con estensione zip e doc. L'IDE non rileva i file che possono essere modificati solo tramite un editor esterno.

## <a name="commands-available-in-the-ide"></a>Comandi disponibili nell'IDE

I menu, le barre degli strumenti e i comandi in essi contenuti cambiano a seconda del formato del file aperto. Quando si apre un file di testo, ad esempio, si apre la barra degli strumenti dell'editor di testo e sono disponibili i relativi comandi. Se in seguito si apre un file XML Schema, viene visualizzata la barra degli strumenti XML Schema. Mentre si modifica l'XML Schema, i comandi della barra degli strumenti dell'editor di testo o la stessa barra degli strumenti non sono disponibili. L'XML Schema è la finestra attiva e di conseguenza ha il contesto della selezione corrente. Quando si passa da un file di progetto a un file esterno non vengono più visualizzati tutti i comandi correlati al progetto ma soltanto quelli direttamente correlati al file esterno.

## <a name="folder-display-options"></a>Opzioni di visualizzazione della cartella

È possibile impostare le opzioni di visualizzazione per la cartella **File esterni** in modo che venga visualizzata anche se non è aperto alcun file esterno. Il file della soluzione non gestisce in modo permanente un elenco di file esterni. Usa una funzionalità facoltativa che permette di memorizzare l'elenco dei file usati di recente (ultimi elementi usati) per ogni utente.

## <a name="see-also"></a>Vedere anche

- [Sviluppare codice in Visual Studio senza progetti o soluzioni](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)
- [Documenti, ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md)
