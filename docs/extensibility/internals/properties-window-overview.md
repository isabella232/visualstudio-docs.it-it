---
title: Panoramica della finestra Proprietà | Microsoft Docs
description: Informazioni sulle interfacce usate per interagire con il Finestra Proprietà nell'IDE Visual Studio in questa panoramica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2377ee69458f3becb94ee79b8cd580fdbb92823d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028943"
---
# <a name="properties-window-overview"></a>Panoramica della finestra Proprietà
La **finestra** Proprietà consente di visualizzare le proprietà per gli oggetti selezionati nei due tipi principali di finestre disponibili nell'ambiente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sviluppo integrato (IDE). Questi due tipi di finestre sono:

- Finestre degli strumenti come Esplora soluzioni, Visualizzazione classi e Visualizzatore oggetti

- Finestre di documento contenenti editor e finestre di progettazione come progettazione moduli, editor XML ed editor HTML

## <a name="using-the-properties-window"></a>Uso della finestra Proprietà
 Nella **finestra** Proprietà vengono visualizzate le proprietà di uno o più elementi selezionati. Se sono selezionati più elementi, viene visualizzata l'intersezione di tutte le proprietà per tutti gli oggetti selezionati.

 Gli eventi correlati a un oggetto selezionato all'interno di una finestra di progettazione del modulo o di un editor HTML che usano metadati COM+ vengono visualizzati nella **finestra** Proprietà. Ad esempio, è possibile selezionare un pulsante e visualizzare gli eventi associati, ad esempio un evento, che `OnClick` può essere collegato a tale pulsante.

 Gli eventi visualizzati nella **finestra Proprietà** vengono usati principalmente con oggetti associati al codice. Se si modifica un formato di file che non ha nulla a che fare con il codice, non verranno generati eventi. Gli eventi vengono visualizzati nella **finestra** Proprietà solo quando è presente un'associazione tra l'esecuzione del codice e determinati eventi associati a oggetti specifici. Un esempio è il code-behind di un oggetto selezionato che viene eseguito quando tale oggetto viene attivato.

 Nella tabella seguente sono elencate le interfacce principali usate dalla **finestra** Proprietà.

|Interface Name (Nome interfaccia)|Descrizione|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornisce un elenco di categorie alla finestra **Proprietà** ed esegue il mapping di ogni proprietà a una categoria.|
|[Interfaccia IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Espone i metodi e le proprietà di un oggetto agli strumenti di programmazione e ad altre applicazioni che supportano l'automazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornisce pulsanti con puntini di sospensione (...) denominati *generatori che* aprono finestre di dialogo modali implementate dall'oggetto stesso. Usato quando un valore non viene digitato facilmente dall'utente in un campo di testo. Ad esempio, può essere usato per aprire un selettore colori che determina automaticamente il valore RGB.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornisce l'accesso agli oggetti utilizzati per aggiornare le informazioni visualizzate nella **finestra** Proprietà. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene implementato da VSPackage per ogni finestra che contiene oggetti selezionabili con proprietà correlate da visualizzare.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornisce informazioni sul tipo di un oggetto, ad esempio i metodi di un'interfaccia e i campi di una struttura.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Consente ai pacchetti VSPackage di ricevere la notifica degli eventi di selezione e di recuperare informazioni sulla gerarchia del progetto corrente, sull'elemento, sul valore dell'elemento e sul contesto dell'interfaccia utente del comando.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornisce l'ambiente con accesso a più selezioni.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usato per fornire nomi localizzati per alcune proprietà visualizzate nella **finestra** Proprietà.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifies ai pacchetti VSPackage registrati le modifiche alla selezione, al valore dell'elemento o al contesto dell'interfaccia utente comandi correnti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica all'ambiente una modifica nella selezione corrente e fornisce l'accesso alle informazioni sulla gerarchia e sugli elementi relativi alla nuova selezione.|

 Per altre informazioni su `IDispatch` , vedere MSDN Library.

## <a name="see-also"></a>Vedi anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
- [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)
