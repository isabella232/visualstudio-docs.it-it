---
title: Finestra della casella degli strumenti
description: Informazioni sulla finestra Casella degli strumenti e su come vengono visualizzati i controlli che è possibile aggiungere Visual Studio progetti.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 068cfa548f2421791e79e9a79f56eb530b9b06aa9cdb3a7951433c2cc3b36e89
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371894"
---
# <a name="toolbox"></a>Casella degli strumenti

Nella finestra **Casella degli strumenti** sono visualizzati i controlli che è possibile aggiungere ai progetti di Visual Studio. Per aprire **la Casella degli** strumenti , **scegliere**  >  **Visualizza** casella degli strumenti dalla barra dei menu o premere **CTRL** + **ALT** + **X.**

![Screenshot della finestra Casella degli strumenti che mostra le opzioni nella sezione Contenitori.](media/vs-2019/toolbox.png "Screenshot della finestra Casella degli strumenti")

È possibile trascinare diversi controlli sulla superficie della finestra di progettazione in uso nonché ridimensionare e posizionare tali controlli.

La casella degli strumenti viene visualizzata insieme alle visualizzazioni della finestra di progettazione, ad esempio la visualizzazione della finestra di progettazione di un file XAML o di Windows di app Form. La **casella degli strumenti** visualizza solo i controlli che possono essere usati nella finestra di progettazione corrente. È possibile eseguire una ricerca all'interno della **casella degli strumenti** per restringere ulteriormente gli elementi visualizzati.

> [!NOTE]
> Per alcuni tipi di progetto, nella **casella degli strumenti** potrebbe non essere visualizzato alcun elemento.

La versione di.NET di destinazione del progetto influisce sul set di controlli visibili nella casella degli strumenti. Se necessario, è possibile modificare la versione del framework di destinazione dalle pagine delle proprietà del progetto. Selezionare il nodo del progetto in **Esplora soluzioni** e quindi scegliere **Progetto** > **Proprietà nomeprogetto** nella barra dei menu. Nella scheda **Applicazione** usare l'elenco a discesa **Framework di destinazione**.

::: moniker range=">=vs-2019"

![Screenshot della finestra di dialogo Applicazione che mostra le opzioni nell'elenco a discesa Framework di destinazione.](media/vs-2019/toolbox-change-dotnet-version.png "Screenshot della finestra di dialogo in cui è possibile modificare la versione di .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Gestire la finestra della casella degli strumenti e i relativi controlli

Per impostazione predefinita, **la casella** degli strumenti viene compressa lungo il lato sinistro dell'IDE Visual Studio e viene visualizzata quando il cursore viene spostato su di esso. È possibile bloccare la **casella degli strumenti**, facendo clic sull'icona **Blocca** nella barra degli strumenti della casella degli strumenti, in modo che resti aperta quando il cursore viene spostato. È anche possibile disancorare la finestra della **casella degli strumenti** e trascinarla in qualsiasi posizione sullo schermo. È possibile ancorare, disancorare e nascondere la **casella degli strumenti** facendo clic con il pulsante destro del mouse sulla relativa barra degli strumenti e scegliendo una delle opzioni.

> [!TIP]
> Se la casella degli strumenti non viene più visualizzata come compressa sul lato sinistro dell'IDE di Visual Studio, è possibile aggiungerla nuovamente scegliendo Reimposta layout finestra dalla barra  >   dei menu.

È possibile ridisporre gli elementi in **una** scheda della casella degli strumenti o aggiungere schede ed elementi personalizzati usando i comandi seguenti nel menu di scelta rapida:

- **Rinomina elemento:** rinomina l'elemento selezionato.

- **Elenco**: visualizza i controlli in un elenco verticale. Se deselezionati, i controlli vengono visualizzati in orizzontale.

- **Mostra tutto**: visualizza tutti i controlli possibili, non solo quelli applicabili alla finestra di progettazione corrente.

- **Scegli elementi**: apre la finestra di dialogo **Scegli elementi della Casella degli strumenti** che consente di specificare gli elementi visualizzati nella **casella degli strumenti**. È possibile visualizzare o nascondere un elemento selezionando o deselezionando la relativa casella di controllo.

- **Ordina elementi alfabeticamente:** ordina gli elementi in base al nome.

- **Reimposta barra degli strumenti**: ripristina le impostazioni e gli elementi predefiniti della **casella degli strumenti**.

- **Aggiungi scheda**: aggiunge una nuova scheda della **casella degli strumenti**.

- **Sposta su**: sposta l'elemento selezionato verso l'alto.

- **Sposta giù**: sposta l'elemento selezionato verso il basso.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Creare e distribuire controlli della casella degli strumenti personalizzati

È possibile creare controlli della **casella degli strumenti** personalizzati partendo da un modello di progetto basato su [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) o [Windows Form](../../extensibility/creating-a-windows-forms-toolbox-control.md). È quindi possibile distribuire il controllo personalizzato ai colleghi del team o pubblicarlo sul Web usando il [programma di installazione dei controlli della casella degli strumenti ](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su alcune delle schede della casella degli strumenti disponibili, vedere i **collegamenti** seguenti:

- [Casella degli strumenti, scheda Dati](../../ide/reference/toolbox-data-tab.md)
- [Casella degli strumenti, Scheda Componenti](../../ide/reference/toolbox-components-tab.md)
- [Casella degli strumenti, Scheda HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Vedi anche

- [Scegli elementi della Casella degli strumenti, Componenti WPF](choose-toolbox-items-wpf-components.md)
