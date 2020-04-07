---
title: Apertura e salvataggio di elementi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706961"
---
# <a name="opening-and-saving-project-items"></a>Apertura e salvataggio di elementi di progetto
Quando si aggiunge un nuovo tipo di progetto, è necessario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestire l'apertura e il salvataggio dei file di progetto nell'ambiente di sviluppo integrato (IDE). Negli argomenti seguenti vengono illustrati i diversi approcci all'apertura e al salvataggio dei file.

## <a name="in-this-section"></a>Contenuto della sezione
- [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Viene fornita una spiegazione dettagliata del modo in cui l'IDE gestisce il comando **Apri file** e il ruolo dei progetti nella risposta a questo comando.

- [Visualizzazione di file tramite il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce il comando **Apri con,** richiedendo l'apertura di un file con una scelta di editor standard.

- [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)

 Vengono fornite istruzioni dettagliate per specificare che i file di un determinato tipo nel progetto devono essere aperti utilizzando un editor specifico del progetto.

- [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)

 Vengono fornite istruzioni dettagliate per specificare come abilitare l'IDE per aprire un editor standard per i file nel tipo di progetto.

- [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)

 Fornisce istruzioni dettagliate per aprire un editor specifico del progetto per un file aperto.

- [Salvataggio di un documento standard](../../extensibility/internals/saving-a-standard-document.md)

 Viene fornita una spiegazione dettagliata del modo in cui l'IDE gestisce i comandi **Salva**, **Salva con nome**e Salva **tutto** per un documento aperto in un editor standard.

- [Salvataggio di un documento personalizzato](../../extensibility/internals/saving-a-custom-document.md)

 Fornisce un diagramma e una spiegazione dettagliata del modo in cui l'IDE gestisce i comandi **Salva**, **Salva con nome**e Salva **tutto** per i documenti aperti in un editor personalizzato.

- [Scelta dell'editor da usare per aprire un file in un progetto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Viene illustrato il processo che segue l'IDE per selezionare l'editor o la finestra di progettazione appropriata per un file.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md)

 Elenca i quattro tipi di editor che l'IDE può ospitare e fornisce le descrizioni di ogni editor.

- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Viene illustrato come i progetti controllano il modo in cui il codice viene compilato e compilato, come vengono aperti gli editor e come vengono formattati gli elementi di progetto.
