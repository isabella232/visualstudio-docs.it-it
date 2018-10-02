---
title: Decisioni di progettazione di tipo di progetto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49f4b198da38a53360efffcdff82daa6fcdb350c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532215"
---
# <a name="project-type-design-decisions"></a>Decisioni di progettazione relative al tipo di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [decisioni di progettazione di tipo di progetto](https://docs.microsoft.com/visualstudio/extensibility/internals/project-type-design-decisions).  
  
Prima di creare un nuovo tipo di progetto, è necessario prendere alcune decisioni di progettazione riguardanti il tipo di progetto. È necessario decidere quali tipi di elementi che contengono i progetti, come verranno resi persistenti i file di progetto e quali modelli dell'impegno verrà utilizzato.  
  
## <a name="project-items"></a>Elementi del progetto  
 Il progetto userà i file o oggetti astratti? Se si usano i file, saranno file basato sul riferimento o basate su directory? Sono il file o oggetti astratti usciti sia locale o remoto?  
  
 Gli elementi in un progetto possono essere file, o possono essere oggetti più astratti, ad esempio gli oggetti in un database repository o le connessioni dati nella rete Internet. Se gli elementi sono file, il progetto può essere un riferimento basato su o un progetto basato su directory.  
  
 Nei progetti in base al riferimento, gli elementi possono comparire in più di un progetto. Tuttavia, il file effettivo che rappresenta un elemento si trova in una directory solo. Nei progetti basati su directory, tutti gli elementi di progetto esistono nella struttura di directory. Per altre informazioni, vedere [NIB: gestione degli elementi nei progetti](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Gli elementi locali vengono archiviati nello stesso computer in cui è installata l'applicazione. Gli elementi remoti possono essere archiviati in un server separato in una rete locale o in un' posizione su Internet.  
  
## <a name="project-file-persistence"></a>Salvataggio permanente dei File progetto  
 I dati vengono archiviati in sistemi comuni di file flat o in un'archiviazione strutturata? Sarà possibile aprire i file usando un editor standard o un editor specifico del progetto?  
  
 Per rendere persistenti i propri dati, la maggior parte delle applicazioni di salvare i dati in un file e quindi leggerlo nuovamente quando un utente deve esaminare o modificare le informazioni.  
  
 Archiviazione strutturata, detta anche file compositi, in genere viene usato quando numerosi oggetti modello COM (Component Object) necessario archiviare i dati resi persistenti in un singolo file. Con archiviazione strutturata, diversi componenti software diversi possono condividere un file singolo disco.  
  
 Sono disponibili diverse opzioni da tenere in considerazione la persistenza per gli elementi nel progetto. È possibile eseguire una delle opzioni seguenti:  
  
-   Salvare ogni file singolarmente quando viene modificata.  
  
-   Acquisire molte transazioni in un'unica **salvare** operazione.  
  
-   Salvare i file in locale, quindi pubblicare in un server o usare un altro approccio per il salvataggio di elementi di progetto quando l'elemento rappresenta una connessione dati a un oggetto remoto.  
  
 Per altre informazioni sulla persistenza, vedere [progetto persistenza](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modello di progetto dell'impegno  
 Verranno aperto gli oggetti dati persistenti in modalità diretta o in modalità transazionale?  
  
 Quando gli oggetti dati vengono aperti in modalità diretta, le modifiche apportate ai dati sono incorporate immediatamente oppure quando l'utente salva manualmente il file.  
  
 Quando gli oggetti dati vengono aperti utilizzando la modalità transazionale, le modifiche vengono salvate in un percorso temporaneo in memoria e non vengono eseguito il commit fino a quando l'utente sceglie manualmente salvare il file. In quel momento, tutte le modifiche devono trovarsi insieme o non verrà apportata alcuna modifica.  
  
## <a name="see-also"></a>Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: gestione degli elementi nei progetti](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistenza del progetto](../../extensibility/internals/project-persistence.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)

