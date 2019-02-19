---
title: File esterni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9b55bc206b204fe2b2e5ef71e2fdb1d48e67802d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54802584"
---
# <a name="miscellaneous-files"></a>File esterni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
È consigliabile usare gli editor [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per lavorare in modo indipendente sui file di un progetto o di una soluzione. Mentre si ha una soluzione aperta, è possibile aprire e modificare i file senza aggiungerli a una soluzione o a un progetto. I file che si intende usare in modo indipendente dai contenitori sono chiamati file esterni. I file esterni sono esterni a soluzioni e progetti, non sono inclusi nelle compilazioni e non possono essere inclusi in una soluzione sotto il controllo del codice sorgente.  
  
 L'apertura dei file in modo indipendente dal contenitore è utile per diversi motivi. Si potrebbe voler visualizzare un file durante lo sviluppo di una soluzione basata su un progetto ma che non è parte integrante dello sviluppo della soluzione. Tra gli esempi comuni vi sono note o istruzioni di sviluppo, lo schema del database e segmenti di codice. L'utente potrebbe anche voler creare un file autonomo.  
  
 ![Progetti di soluzioni](../../ide/reference/media/projects-solutions-misc.gif "Projects_Solutions_Misc")  
  
 Esplora soluzioni può visualizzare una cartella File esterni per i file se sono abilitate le opzioni per la cartella. È possibile impostare le opzioni da [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md). Dopo la chiusura di un file esterno, esso non è associato ad alcuna soluzione o progetto particolare a meno che non sia stata abilitata un'opzione a tale scopo.  
  
 La cartella File esterni rappresenta i file come collegamenti. Sebbene questa cartella non sia parte di una soluzione, quando si apre una soluzione alcuni o tutti i file esterni che sono stati aperti quando la soluzione è stata chiusa l'ultima volta vengono aperti nuovamente, in base alle impostazioni per la cartella.  
  
> [!NOTE]
>  Alcuni dei file che non vengono visualizzati nella cartella File esterni sono file che non possono essere modificati all'interno dell'IDE, ad esempio file con estensione zip e doc. L'IDE non rileverà i file che possono essere modificati solo tramite un editor esterno.  
  
## <a name="commands-available-in-the-ide"></a>Comandi disponibili nell'IDE  
 I menu, le barre degli strumenti e i comandi in essi contenuti cambiano a seconda del formato del file aperto. Quando si apre un file di testo, ad esempio, si apre la barra degli strumenti dell'editor di testo e sono disponibili i relativi comandi. Se in seguito si apre un file XML Schema, viene visualizzata la barra degli strumenti XML Schema. Mentre si modifica l'XML Schema, i comandi della barra degli strumenti dell'editor di testo o la stessa barra degli strumenti non sono disponibili. L'XML Schema è la finestra attiva e di conseguenza ha il contesto della selezione corrente. Quando si passa da un file di progetto a un file esterno non vengono più visualizzati tutti i comandi correlati al progetto ma soltanto quelli direttamente correlati al file esterno.  
  
## <a name="folder-display-options"></a>Opzioni di visualizzazione cartella  
 È possibile impostare le opzioni di visualizzazione della cartella File esterni in modo che la cartella venga visualizzata anche se non è aperto alcun file esterno. Il file della soluzione non gestisce in modo permanente un elenco di file esterni. Usa una funzionalità facoltativa che consente di ricordare l'elenco dei file usati di recente (MRU) per ogni utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md)  (Soluzioni e progetti)  
 [Documents, Environment, Options Dialog Box](../../ide/reference/documents-environment-options-dialog-box.md) (Documenti, Ambiente, finestra di dialogo Opzioni)
