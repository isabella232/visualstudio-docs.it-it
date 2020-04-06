---
title: Decisioni di progettazione del tipo di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706366"
---
# <a name="project-type-design-decisions"></a>Decisioni di progettazione relative al tipo di progetto
Prima di creare un nuovo tipo di progetto, è necessario prendere diverse decisioni di progettazione relative al tipo di progetto. È necessario decidere quali tipi di elementi conterrà i progetti, come i file di progetto verranno resi persistenti e quale modello di impegno verrà utilizzato.

## <a name="project-items"></a>Elementi del progetto
 Il progetto utilizzerà file o oggetti astratti? Se si utilizzano file, saranno file basati su riferimenti o directory? I file o gli oggetti astratti saranno locali o remoti?

 The items in a project can be files, or they can be more abstract objects such as objects in a database repository or data connections across the Internet. Se gli elementi sono file, il progetto può essere basato su riferimenti o su directory.

 Nei progetti basati su riferimenti, gli elementi possono essere visualizzati in più progetti. Tuttavia, il file effettivo rappresentato da un elemento si trova in una sola directory. Nei progetti basati su directory, tutti gli elementi di progetto sono presenti nella struttura di directory.

 Gli elementi locali vengono archiviati nello stesso computer in cui è installata l'applicazione. Gli elementi remoti possono essere archiviati in un server separato in una rete locale o in un altro punto di Internet.

## <a name="project-file-persistence"></a>Persistenza dei file di progettoProject File Persistence
 I dati verranno archiviati in file system flat comuni o in archiviazione strutturata? I file verranno aperti utilizzando un editor standard o un editor specifico del progetto?

 Per rendere persistenti i dati, la maggior parte delle applicazioni salva i dati in un file e quindi li rilegge quando un utente deve rivedere o modificare le informazioni.

 L'archiviazione strutturata, denominata anche file composti, viene in genere utilizzata quando diversi oggetti COM (Component Object Model) devono archiviare i dati persistenti in un singolo file. Con l'archiviazione strutturata, diversi componenti software diversi possono condividere un singolo file su disco.

 Sono disponibili diverse opzioni da considerare per quanto riguarda la persistenza per gli elementi nel progetto. È possibile eseguire una delle seguenti opzioni:

- Salvare ogni file singolarmente quando è stato modificato.

- Acquisire molte transazioni in una singola operazione **di salvataggio.**

- Salvare i file in locale e quindi pubblicare in un server o utilizzare un altro approccio per salvare gli elementi di progetto quando l'elemento rappresenta una connessione dati a un oggetto remoto.

  Per ulteriori informazioni sulla persistenza, vedere [Persistenza del progetto](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Modello di impegno del progetto
 Gli oggetti dati persistenti verranno aperti in modalità diretta o transazionale?

 Quando gli oggetti dati vengono aperti in modalità diretta, le modifiche apportate ai dati vengono incorporate immediatamente o quando l'utente salva manualmente il file.

 Quando gli oggetti dati vengono aperti utilizzando la modalità transazionale, le modifiche vengono salvate in una posizione temporanea in memoria e non viene eseguito il commit fino a quando l'utente non sceglie manualmente di salvare il file. A quel punto, tutte le modifiche devono avvenire insieme o non verranno apportate modifiche.

## <a name="see-also"></a>Vedere anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Salvataggio permanente dei progetti](../../extensibility/internals/project-persistence.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)
- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)
- [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)
