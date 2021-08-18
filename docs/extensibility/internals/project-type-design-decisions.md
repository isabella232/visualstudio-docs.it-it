---
title: Project Decisioni di progettazione dei tipi | Microsoft Docs
description: Informazioni sull'elemento, sulla persistenza dei file di progetto e sulle decisioni di progettazione del meccanismo di impegno da prendere prima di estendere Visual Studio creando un nuovo tipo di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b22ea9e537adaf0c6178b5c9f7aff1702b84bbcd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102376"
---
# <a name="project-type-design-decisions"></a>Decisioni di progettazione relative al tipo di progetto
Prima di creare un nuovo tipo di progetto, è necessario prendere diverse decisioni di progettazione relative al tipo di progetto. È necessario decidere quali tipi di elementi saranno contenuti nei progetti, come verranno mantenuti i file di progetto e quale modello di impegno verrà utilizzato.

## <a name="project-items"></a>Elementi del progetto
 Il progetto userà file o oggetti astratti? Se si usano file, saranno file basati su riferimento o basati su directory? I file o gli oggetti astratti saranno locali o remoti?

 Gli elementi in un progetto possono essere file o essere oggetti più astratti, ad esempio oggetti in un repository di database o connessioni dati in Internet. Se gli elementi sono file, il progetto può essere un progetto basato su riferimento o basato su directory.

 Nei progetti basati su riferimenti gli elementi possono essere visualizzati in più progetti. Tuttavia, il file effettivo rappresentato da un elemento si trova in una sola directory. Nei progetti basati su directory tutti gli elementi di progetto sono presenti nella struttura di directory.

 Gli elementi locali vengono archiviati nello stesso computer in cui è installata l'applicazione. Gli elementi remoti possono essere archiviati in un server separato in una rete locale o in un'altra posizione su Internet.

## <a name="project-file-persistence"></a>Project Persistenza dei file
 I dati verranno archiviati in file system flat comuni o in un archivio strutturato? I file verranno aperti usando un editor standard o un editor specifico del progetto?

 Per rendere persistenti i dati, la maggior parte delle applicazioni salva i dati in un file e quindi legge i dati quando un utente deve rivedere o modificare le informazioni.

 L'archiviazione strutturata, detta anche file composti, viene in genere usata quando diversi oggetti Component Object Model (COM) devono archiviare i dati persistenti in un singolo file. Con l'archiviazione strutturata, diversi componenti software possono condividere un singolo file su disco.

 Sono disponibili diverse opzioni da prendere in considerazione per la persistenza per gli elementi nel progetto. È possibile eseguire una delle opzioni seguenti:

- Salvare ogni file singolarmente dopo che è stato modificato.

- Acquisire molte transazioni in una singola operazione **di** salvataggio.

- Salvare i file in locale e quindi pubblicare in un server o usare un altro approccio per salvare gli elementi di progetto quando l'elemento rappresenta una connessione dati a un oggetto remoto.

  Per altre informazioni sulla persistenza, vedere [Project Persistence](../../extensibility/internals/project-persistence.md) e Opening and Saving [Project Items](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Project Modello di impegno
 Gli oggetti dati persistenti verranno aperti in modalità diretta o in modalità transazione?

 Quando gli oggetti dati vengono aperti in modalità diretta, le modifiche apportate ai dati vengono incorporate immediatamente o quando l'utente salva manualmente il file.

 Quando gli oggetti dati vengono aperti in modalità transazione, le modifiche vengono salvate in un percorso temporaneo in memoria e non ne viene eseguito il commit fino a quando l'utente non sceglie manualmente di salvare il file. In quel momento, tutte le modifiche devono essere eseguite insieme o non verrà apportata alcuna modifica.

## <a name="see-also"></a>Vedi anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Salvataggio permanente dei progetti](../../extensibility/internals/project-persistence.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)
- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)
- [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)
