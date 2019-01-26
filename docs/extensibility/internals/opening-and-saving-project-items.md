---
title: Apertura e salvataggio di elementi di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a7c9cae59bc5a02dcca53afb66c234012e6713
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918681"
---
# <a name="opening-and-saving-project-items"></a>Apertura e salvataggio di elementi di progetto
Quando si aggiunge un nuovo tipo di progetto, è necessario gestire l'apertura e salvataggio dei file di progetti nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Gli argomenti seguenti descrivono i diversi approcci per l'apertura e salvataggio di file.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce i **Apri File** comando e il ruolo di progetti in risposta a questo comando.  
  
 [Visualizzazione di file tramite il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Fornisce una spiegazione dettagliata e dettagliata del modo in cui l'IDE gestisce i **aperta con** comando, che richiede l'apertura di un file con alcune scelte degli editor standard.  
  
 [Procedura: Apri editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)  
 Vengono fornite istruzioni dettagliate che consentono di specificare che i file di un determinato tipo nel progetto devono essere aperto usando un editor specifico del progetto.  
  
 [Procedura: Aprire gli editor Standard](../../extensibility/how-to-open-standard-editors.md)  
 Vengono fornite istruzioni dettagliate per la specifica come abilitare l'IDE aprire un editor standard per i file nel tipo di progetto.  
  
 [Procedura: Aprire gli editor per i documenti aperti](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Vengono fornite istruzioni dettagliate per aprire un editor specifico del progetto per un file aperto.  
  
 [Salvataggio di un documento standard](../../extensibility/internals/saving-a-standard-document.md)  
 Fornisce una spiegazione dettagliata del modo in cui l'IDE gestisce i **salvare**, **Salva con nome**, e **Salva tutto** comandi per un documento aperto in un editor standard.  
  
 [Salvataggio di un documento personalizzato](../../extensibility/internals/saving-a-custom-document.md)  
 Fornisce un diagramma e una spiegazione dettagliata del modo in cui l'IDE gestisce i **salvare**, **Salva con nome**, e **Salva tutto** comandi per i documenti aperti in un editor personalizzato.  
  
 [Scelta dell'editor da usare per aprire un file in un progetto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Illustra il processo che l'IDE deve seguire per selezionare la finestra di progettazione per un file o l'editor appropriato.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di finestre di progettazione ed editor personalizzati](../../extensibility/creating-custom-editors-and-designers.md)  
 Elenca i quattro tipi di editor che l'IDE può ospitare e fornisce le descrizioni di ogni editor.  
  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Illustra come progetti consentono di controllare la modalità di codice viene compilato e creato, come aprire gli editor e come formattare gli elementi del progetto.