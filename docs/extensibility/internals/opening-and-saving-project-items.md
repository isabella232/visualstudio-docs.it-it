---
title: Apertura e salvataggio Project elementi | Microsoft Docs
description: Informazioni sui diversi approcci per l'apertura e il salvataggio di file per il nuovo tipo di progetto nell Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7cdf47d983d7070c0cc1a407a5a32f6e661b36cb85ef0310d06be112c2cb0816
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359299"
---
# <a name="opening-and-saving-project-items"></a>Apertura e salvataggio di elementi di progetto
Quando si aggiunge un nuovo tipo di progetto, è necessario gestire l'apertura e il salvataggio dei file di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nell'ambiente di sviluppo integrato (IDE). Negli argomenti seguenti vengono illustrati i diversi approcci per l'apertura e il salvataggio di file.

## <a name="in-this-section"></a>Contenuto della sezione
- [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce il comando **Apri file** e del ruolo dei progetti nella risposta a questo comando.

- [Visualizzazione di file tramite il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fornisce una spiegazione dettagliata e dettagliata del modo in cui l'IDE gestisce il comando **Apri** con, richiedendo l'apertura di un file con una scelta di editor standard.

- [Procedura: Aprire gli editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)

 Fornisce istruzioni dettagliate per specificare che i file di un determinato tipo nel progetto devono essere aperti tramite un editor specifico del progetto.

- [Procedura: Aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)

 Fornisce istruzioni dettagliate per specificare come consentire all'IDE di aprire un editor standard per i file nel tipo di progetto.

- [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)

 Fornisce istruzioni dettagliate per aprire un editor specifico del progetto per un file aperto.

- [Salvataggio di un documento standard](../../extensibility/internals/saving-a-standard-document.md)

 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce i comandi **Salva** **,** Salva con nome e Salva tutto per un documento aperto in un editor standard. 

- [Salvataggio di un documento personalizzato](../../extensibility/internals/saving-a-custom-document.md)

 Fornisce un diagramma e una spiegazione dettagliata del modo in  cui l'IDE gestisce i comandi **Salva** **,** Salva con nome e Salva tutto per i documenti aperti in un editor personalizzato.

- [Scelta dell'editor da usare per aprire un file in un progetto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Illustra il processo seguito dall'IDE per selezionare l'editor o la finestra di progettazione appropriata per un file.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md)

 Elenca i quattro tipi di editor che l'IDE può ospitare e fornisce le descrizioni di ogni editor.

- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene illustrato come i progetti controllano il modo in cui il codice viene compilato e compilato, come vengono aperti gli editor e come vengono formattati gli elementi del progetto.
