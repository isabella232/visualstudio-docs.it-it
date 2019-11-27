---
title: Uso della casella degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba8a37ac9e049455ffe19314dee0e228c3c14c97
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295604"
---
# <a name="using-the-toolbox"></a>Utilizzo della Casella degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare la casella degli strumenti per aggiungere controlli e altri elementi al progetto. È possibile trascinare diversi controlli sulla superficie della finestra di progettazione in uso nonché ridimensionare e posizionare tali controlli.

 La casella degli strumenti viene visualizzata insieme alle visualizzazioni delle finestre di progettazione, ad esempio la visualizzazione Progettazione di un file XAML. La casella degli strumenti visualizza solo i controlli che possono essere usati nella finestra di progettazione corrente.

 La versione di.NET Framework di destinazione del progetto influisce sul set di controlli visibili nella casella degli strumenti. Per impostazione predefinita, i progetti [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] hanno come destinazione .NET Framework 4.5.1. È possibile impostare come destinazione del progetto una versione diversa di .NET Framework selezionando il nodo del progetto in **Esplora soluzioni** e quindi passando a **Properties/Application/Target Framework**.

## <a name="managing-the-toolbox-and-its-controls"></a>Gestione della casella degli strumenti e dei relativi controlli
 Per impostazione predefinita, la casella degli strumenti viene compressa lungo la parte sinistra dell'IDE di Visual Studio e viene visualizzata quando il cursore viene spostato su di essa. È possibile bloccare la casella degli strumenti, facendo clic sull'icona **Blocca** nella barra degli strumenti della casella degli strumenti, in modo che resti aperta quando il cursore viene spostato. È anche possibile disancorare la finestra della casella degli strumenti e trascinarla in qualsiasi posizione sullo schermo. È possibile ancorare, disancorare e nascondere la casella degli strumenti facendo clic con il pulsante destro del mouse sulla barra degli strumenti della casella degli strumenti e selezionando una delle opzioni.

 È possibile riordinare gli elementi di una scheda della casella degli strumenti o aggiungere schede ed elementi personalizzati usando i seguenti comandi del menu di scelta rapida:

- **Rinomina elemento**: rinomina l'elemento selezionato.

- **Mostra tutto**: visualizza tutti i controlli possibili, non solo quelli applicabili alla finestra di progettazione corrente.

- **Elenco**: visualizza i controlli in un elenco verticale. Se deselezionati, i controlli vengono visualizzati in orizzontale.

- **Scegli elementi**: apre la finestra di dialogo **Scegli elementi della Casella degli strumenti** che consente di specificare gli elementi visualizzati nella **casella degli strumenti**. È possibile visualizzare o nascondere un elemento selezionando o deselezionando la relativa casella di controllo.

- **Ordina elementi alfabeticamente**: ordina gli elementi per nome.

- **Reimposta barra degli strumenti**: ripristina le impostazioni e gli elementi predefiniti della casella degli strumenti.

- **Aggiungi scheda**: aggiunge una nuova scheda della casella degli strumenti.

- **Sposta su**: sposta l'elemento selezionato verso l'alto.

- **Sposta giù**: sposta l'elemento selezionato verso il basso.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Creare e distribuire controlli della casella degli strumenti personalizzati
 È possibile creare un controllo della casella degli strumenti personalizzato in Visual Basic o in Visual C# iniziando con un modello di progetto basato su [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) o [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md). È quindi possibile distribuire il controllo ai colleghi del team o pubblicarlo sul Web usando il [programma di installazione dei controlli della casella degli strumenti ](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).
