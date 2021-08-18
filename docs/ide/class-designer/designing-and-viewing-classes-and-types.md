---
title: Usare Progettazione classi
description: Informazioni su come progettare, visualizzare ed eseguire il refactoring di classi e altri tipi nel codice con Progettazione classi in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7c00a4a92cd91c7a9b2faee614d610c916e3bc90
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056446"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Progettare e visualizzare classi e tipi con Progettazione classi

Progettare, visualizzare ed eseguire il refactoring di classi e altri tipi nel codice **con** Progettazione classi in Visual Studio. Usare i diagrammi classi per creare e modificare classi nel progetto C#, Visual Basic o C++. È anche possibile usare i diagrammi classi per comprendere meglio la struttura del progetto o riorganizzare il codice.

>[!NOTE]
>Progettazione classi non è disponibile nei progetti .NET Core.

## <a name="what-you-can-do-with-class-diagrams"></a>Operazioni eseguibili con i diagrammi classi

- **Progettare**: cambiare il codice del progetto modificando il diagramma classi. Aggiungere nuovi elementi ed eliminare quelli non desiderati. Le modifiche verranno riflesse nel codice.

- **Visualizzare**: comprendere meglio la struttura del progetto visualizzando le classi del progetto in un diagramma. Personalizzare il diagramma in modo da potersi concentrare sui dettagli del progetto a cui si è più interessati. Salvare il diagramma da usare in seguito a scopo dimostrativo o come documentazione.

- **Effettuare il refactoring**: eseguire l'override dei metodi, rinominare gli identificatori, effettuare il refactoring dei parametri e implementare interfacce e classi astratte.

## <a name="view-types-and-relationships"></a>Visualizzare tipi e relazioni

I diagrammi classi visualizzano i dettagli dei tipi, ad esempio i membri che li costituiscono e le relazioni tra gli stessi. La visualizzazione di queste entità è una visualizzazione dinamica nel codice. Ciò significa che è possibile modificare i tipi nella finestra di progettazione e quindi visualizzare le modifiche riflesse nel codice sorgente dell'entità. Analogamente, il diagramma classi viene mantenuto sincronizzato con le modifiche apportate ai file di codice.

> [!NOTE]
> Se il progetto contiene un diagramma classi e fa riferimento a un tipo che si trova in un altro progetto, il diagramma classi non visualizza il tipo di riferimento fino a quando non si compila il progetto per quel tipo. Allo stesso modo, il diagramma non visualizza le modifiche apportate al codice dell'entità esterna fino a quando non si ricompila il progetto per l'entità.

## <a name="class-diagram-workflow"></a>Flusso di lavoro del diagramma classi

I diagrammi classi consentono di comprendere la struttura di classi dei progetti. I progetti potrebbero essere stati creati da altri sviluppatori oppure è semplicemente necessario un aggiornamento su un progetto creato personalmente. È possibile usare i diagrammi classi per personalizzare, condividere e presentare informazioni sui progetti ad altri utenti.

La prima fase della presentazione di informazioni sui progetti consiste nella creazione di un diagramma classi che comprenda gli elementi da visualizzare. Per altre informazioni, vedere [Aggiungere un diagramma classi](how-to-add-class-diagrams-to-projects.md). È possibile creare più diagrammi classi per un progetto, da usare per mostrare una visualizzazione distinta del progetto, un subset scelto dei tipi del progetto oppure un subset scelto dei membri dei tipi.

Oltre a definire ciò che visualizza ogni diagramma classi, è anche possibile modificare il modo in cui vengono presentate le informazioni. Per altre informazioni, vedere [Procedura: Personalizzare i diagrammi classi](how-to-customize-class-diagrams.md).

Dopo aver ottimizzato uno o più diagrammi classi, è possibile copiarli in documenti di Microsoft Office e stamparli oppure esportarli come file di immagine. Per altre informazioni, vedere [Procedura: Copiare elementi dei diagrammi classi in un documento di Microsoft Office](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Procedura: Stampare diagrammi classi](how-to-print-class-diagrams.md) e [Procedura: Esportare diagrammi classi come immagini](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Progettazione classi non tiene traccia del percorso dei file di origine. Di conseguenza, se si modifica la struttura del progetto o si spostano i file di origine in un progetto, Progettazione classi può perdere traccia del tipo, soprattutto del tipo di origine di un typedef, delle classi di base o dei tipi di associazione. Si potrebbe ricevere un errore, ad esempio **Progettazione classi: impossibile visualizzare il tipo**. In tal caso, trascinare di nuovo il codice sorgente modificato o riposizionato nel diagramma classi per visualizzarlo nuovamente.

## <a name="see-also"></a>Vedi anche

- [Funzionalità dell'editor del codice](../writing-code-in-the-code-and-text-editor.md)
- [Eseguire il mapping delle dipendenze nelle soluzioni](../../modeling/map-dependencies-across-your-solutions.md)
