---
title: Scegli elementi della Casella degli strumenti, Componenti WPF
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 731fe05e90e01c60f0a7ff3a14917d6d7625bc1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570557"
---
# <a name="choose-toolbox-items-wpf-components"></a>Scegli elementi della Casella degli strumenti, Componenti WPF

Questa scheda della finestra di dialogo **Scegli elementi della Casella degli strumenti** include l'elenco dei controlli Windows Presentation Foundation (WPF) disponibili nel computer locale. Per visualizzare questo elenco, **scegliere Scegli elementi della casella degli** strumenti dal menu **strumenti** per visualizzare la finestra di dialogo **Scegli elementi della casella degli strumenti** e quindi selezionare la scheda **Componenti WPF** . Per ordinare i componenti elencati, selezionare un'intestazione di colonna.

- Quando la casella di controllo accanto a un componente è selezionata, l'icona di tale componente viene visualizzata nella **casella degli strumenti**.

    > [!TIP]
    > Per aggiungere un controllo WPF a un documento del progetto aperto per la modifica, trascinare l'icona della **casella degli strumenti** corrispondente nell'area di visualizzazione Progettazione. Il codice e il markup predefiniti del componente vengono inseriti nel progetto e sono pronti per la modifica. Per altre informazioni, vedere [Casella degli strumenti](../../ide/reference/toolbox.md).

- Quando la casella di controllo accanto a un componente viene deselezionata, l'icona corrispondente viene rimossa dalla **casella degli strumenti**.

    > [!NOTE]
    > I componenti .NET installati sul computer restano disponibili anche se le icone corrispondenti non sono visualizzate nella **casella degli strumenti**.

Le colonne della scheda **Componenti WPF** contengono le informazioni seguenti:

**Name**

Elenca i nomi dei controlli WPF per i quali sono presenti voci nel Registro di sistema del computer.

**Spazio dei nomi**

Visualizza la gerarchia dello spazio dei nomi [API di .NET](/dotnet/api/?view=netframework-4.7) che definisce la struttura del componente. Ordinare in base a questa colonna per elencare i componenti disponibili in ogni spazio dei nomi .NET installato nel computer in uso.

**Nome assembly**

Visualizza il nome dell'assembly .NET che include lo spazio dei nomi per ogni componente. Ordinare in base a questa colonna per elencare gli spazi dei nomi presenti in ogni assembly .NET installato nel computer in uso.

**Directory**

Visualizza il percorso dell'assembly .NET. Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache. Per altre informazioni sulla cartella Global Assembly Cache, vedere [Usare gli assembly e la Global Assembly Cache](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

### <a name="filter"></a>Filtro

Filtra l'elenco dei controlli WPF in base alla stringa immessa nella casella di testo. Vengono visualizzate tutte le corrispondenze presenti in una qualsiasi delle quattro colonne.

**Cancella**

Cancella la stringa del filtro.

**Sfoglia**

Apre la finestra di dialogo **Apri** che consente di selezionare gli assembly che contengono i controlli WPF. Usare questo metodo per caricare gli assembly che non si trovano nella cartella Global Assembly Cache.

**Lingua**

Visualizza la lingua localizzata dell'assembly che contiene il controllo WPF selezionato.

## <a name="limitations"></a>Limitazioni

L'aggiunta di un controllo personalizzato o di <xref:System.Windows.Controls.UserControl> alla casella degli strumenti presenta le limitazioni seguenti:

- Funziona solo per controlli personalizzati definiti all'esterno del progetto corrente.

- Non si aggiorna correttamente quando la configurazione della soluzione viene modificata da Debug a Release o da Release a Debug. Questo accade perché il riferimento non è un riferimento al progetto, ma è destinato all'assembly sul disco. Se il controllo fa parte della soluzione corrente, quando si passa da Debug a Release il progetto continua a fare riferimento alla versione Debug del controllo.

Inoltre se al controllo personalizzato vengono applicati i metadati della fase di progettazione e tali metadati specificano che [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) è impostato su `false`, il controllo non viene visualizzato nella casella degli strumenti.

È possibile fare riferimento ai controlli direttamente in XAML eseguendo il mapping dello spazio dei nomi e dell'assembly per il controllo.

## <a name="see-also"></a>Vedere anche

- [Casella degli strumenti](../../ide/reference/toolbox.md)
- [Guida introduttiva a WPF](../../designers/getting-started-with-wpf.md)
