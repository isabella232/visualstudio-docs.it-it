---
title: Scegli elementi della Casella degli strumenti, Componenti WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c7967635d8e5d64907587fcd1a9b4d84a31d569
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660920"
---
# <a name="choose-toolbox-items-wpf-components"></a>Scegli elementi della Casella degli strumenti, Componenti WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa scheda della finestra di dialogo **Scegli elementi della Casella degli strumenti** include l'elenco dei controlli Windows Presentation Foundation (WPF) disponibili nel computer locale. Per visualizzare questo elenco, **scegliere Scegli elementi della casella degli** strumenti dal menu **strumenti** per visualizzare la finestra di dialogo **Scegli elementi della casella degli strumenti** e quindi selezionare la scheda **Componenti WPF** . Per ordinare i componenti elencati, selezionare un'intestazione di colonna.

- Quando la casella di controllo accanto a un componente è selezionata, l'icona di tale componente viene visualizzata nella **casella degli strumenti**.

  > [!TIP]
  > Per aggiungere un'istanza di un controllo WPF a un documento del progetto aperto per la modifica, trascinare l'icona della **casella degli strumenti** corrispondente nell'area di visualizzazione Progettazione. Il codice e il markup predefiniti del componente vengono inseriti nel progetto e sono pronti per la modifica. Per altre informazioni, vedere [Procedura: gestire la finestra Casella degli strumenti](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) e [Procedura: modificare le schede della Casella degli strumenti](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Quando la casella di controllo accanto a un componente viene deselezionata, l'icona corrispondente viene rimossa dalla **casella degli strumenti**.

  > [!NOTE]
  > I componenti .NET Framework installati sul computer restano disponibili anche se le icone corrispondenti non sono visualizzate nella **casella degli strumenti**.

  Le colonne della scheda **Componenti WPF** contengono le informazioni seguenti:

  Nome elenca i nomi dei controlli WPF per cui sono presenti voci nel registro di sistema del computer.

  Spazio dei nomi Visualizza la gerarchia dello spazio dei nomi [.NET Framework libreria di classi](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) che definisce la struttura del componente. Ordinare in base a questa colonna per elencare i componenti disponibili in ogni spazio dei nomi .NET Framework installato nel computer in uso.

  Nome assembly consente di visualizzare il nome dell'assembly .NET Framework che include lo spazio dei nomi per ogni componente. Ordinare in base a questa colonna per elencare gli spazi dei nomi presenti in ogni assembly .NET Framework installato nel computer in uso.

  Directory Visualizza il percorso dell'assembly .NET Framework. Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache. Per altre informazioni sulla cartella Global Assembly Cache, vedere [Utilizzo di assembly e della Global Assembly Cache](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Filtro** di Filtra l'elenco di controlli WPF in base alla stringa fornita nella casella di testo. Vengono visualizzate tutte le corrispondenze presenti in una qualsiasi delle quattro colonne.

 **Cancella** Cancella la stringa di filtro.

 **Sfoglia** Apre la finestra di dialogo **Apri** , che consente di passare agli assembly che contengono i controlli WPF. Usare questo metodo per caricare gli assembly che non si trovano nella cartella Global Assembly Cache.

 **Lingua** di Mostra la lingua localizzata dell'assembly che contiene il controllo WPF selezionato.

## <a name="limitations"></a>Limitazioni
 L'aggiunta di un controllo personalizzato o di <xref:System.Windows.Controls.UserControl> alla casella degli strumenti presenta le limitazioni seguenti.

- Funziona solo per controlli personalizzati definiti all'esterno del progetto corrente.

- Non si aggiorna correttamente quando la configurazione della soluzione viene modificata da Debug a Release o da Release a Debug. Questo accade perché il riferimento non è un riferimento al progetto, ma è destinato all'assembly sul disco. Se il controllo fa parte della soluzione corrente, quando si passa da Debug a Release il progetto continua a fare riferimento alla versione Debug del controllo.

  Inoltre, se al controllo personalizzato vengono applicati i metadati della fase di progettazione e questi metadati specificano che [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) è impostato su `false` , il controllo non viene visualizzato nella casella degli strumenti.

  È possibile fare riferimento ai controlli direttamente in XAML eseguendo il mapping dello spazio dei nomi e dell'assembly per il controllo. Per altre informazioni, vedere [Procedura: importare uno spazio dei nomi in XAML](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Scegli elementi della Casella degli strumenti (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Casella degli strumenti](../../ide/reference/toolbox.md)
- [Procedura: utilizzare un controllo WPF di terze parti in un'applicazione WPF](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [WPF Designer](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)