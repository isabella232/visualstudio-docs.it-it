---
title: Decisioni di progettazione del tipo di progetto | Microsoft Docs
description: Per informazioni sull'elemento, sulla persistenza dei file di progetto e sulle decisioni di progettazione del meccanico di impegno, vedere prima di estendere Visual Studio creando un nuovo tipo di progetto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1b051abfede6ec90350878f669ed32e7e26b299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896758"
---
# <a name="project-type-design-decisions"></a>Decisioni di progettazione relative al tipo di progetto
Prima di creare un nuovo tipo di progetto, è necessario prendere alcune decisioni di progettazione per il tipo di progetto. È necessario decidere quali tipi di elementi saranno contenuti nei progetti, come verranno salvati in modo permanente i file di progetto e il modello di impegno che verrà usato.

## <a name="project-items"></a>Elementi del progetto
 Il progetto utilizzerà file o oggetti astratti? Se si usano i file, saranno file basati su riferimenti o basati su directory? I file o gli oggetti astratti saranno locali o remoti?

 Gli elementi di un progetto possono essere file oppure possono essere più oggetti astratti, ad esempio oggetti in un repository di database o connessioni dati su Internet. Se gli elementi sono file, il progetto può essere basato su riferimenti o su un progetto basato su directory.

 Nei progetti basati su riferimenti, gli elementi possono essere visualizzati in più di un progetto. Tuttavia, il file effettivo rappresentato da un elemento si trova in una sola directory. Nei progetti basati su directory tutti gli elementi del progetto sono presenti nella struttura di directory.

 Gli elementi locali vengono archiviati nello stesso computer in cui è installata l'applicazione. Gli elementi remoti possono essere archiviati in un server separato in una rete locale o in un'altra posizione su Internet.

## <a name="project-file-persistence"></a>Persistenza file di progetto
 I dati verranno archiviati in file System Flat comuni o nell'archiviazione strutturata? I file verranno aperti usando un editor standard o un editor specifico del progetto?

 Per salvare in modo permanente i dati, la maggior parte delle applicazioni Salva i dati in un file e quindi li legge quando un utente deve rivedere o modificare le informazioni.

 L'archiviazione strutturata, nota anche come file composti, viene in genere usata quando più oggetti Component Object Model (COM) devono archiviare i dati salvati in modo permanente in un unico file. Con l'archiviazione strutturata, diversi componenti software possono condividere un singolo file su disco.

 Sono disponibili diverse opzioni da considerare per quanto riguarda la persistenza per gli elementi del progetto. È possibile eseguire una delle opzioni seguenti:

- Salvare ogni file singolarmente quando è stato modificato.

- Acquisire molte transazioni in un'unica operazione di **salvataggio** .

- Salvare i file localmente, quindi pubblicarli in un server o usare un altro approccio per salvare gli elementi di progetto quando l'elemento rappresenta una connessione dati a un oggetto remoto.

  Per ulteriori informazioni sulla persistenza, vedere [persistenza del progetto](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Modello di impegno del progetto
 Gli oggetti dati salvati in modo permanente verranno aperti in modalità diretta o in modalità transazionale?

 Quando gli oggetti dati vengono aperti in modalità diretta, le modifiche apportate ai dati vengono incorporate immediatamente o quando l'utente salva manualmente il file.

 Quando gli oggetti dati vengono aperti usando la modalità transazionale, le modifiche vengono salvate in un percorso temporaneo in memoria e non vengono salvate fino a quando l'utente sceglie di salvare il file manualmente. A questo punto, tutte le modifiche devono essere eseguite insieme o non verrà apportata alcuna modifica.

## <a name="see-also"></a>Vedi anche
- [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Salvataggio permanente dei progetti](../../extensibility/internals/project-persistence.md)
- [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)
- [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)
- [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)
