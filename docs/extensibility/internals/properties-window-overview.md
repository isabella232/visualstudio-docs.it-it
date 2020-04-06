---
title: Cenni preliminari sulla finestra Proprietà . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706027"
---
# <a name="properties-window-overview"></a>Panoramica della finestra Proprietà
Il **proprietà** finestra viene utilizzata per visualizzare le proprietà per gli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oggetti selezionati nei due tipi principali di finestre disponibili nell'ambiente di sviluppo integrato (IDE). Questi due tipi di finestre sono:

- Finestre degli strumenti, ad esempio Esplora soluzioni, Visualizzazione classi e Visualizzatore oggetti

- Finestre di documento contenenti tali editor e finestre di progettazione come la finestra di progettazione dei moduli, l'editor XML e l'editor HTML

## <a name="using-the-properties-window"></a>Utilizzo della finestra Proprietà
 Nella finestra **Proprietà** vengono visualizzate le proprietà di uno o più elementi selezionati. Se sono selezionati più elementi, viene visualizzata l'intersezione di tutte le proprietà per tutti gli oggetti selezionati.

 Gli eventi correlati a un oggetto selezionato all'interno di una finestra di progettazione di un modulo o di un editor HTML che utilizza metadati COM, vengono visualizzati nella finestra **Proprietà.** Ad esempio, è possibile selezionare un pulsante `OnClick` e visualizzare gli eventi associati, ad esempio un evento, che può essere collegato a tale pulsante.

 Gli eventi visualizzati nella finestra **Proprietà** vengono utilizzati principalmente con gli oggetti associati al codice. Se si sta modificando un formato di file che non ha nulla a che fare con il codice, non si avrà alcun evento. Gli eventi vengono visualizzati nella finestra **Proprietà** solo quando è presente un'associazione tra il codice in esecuzione e determinati eventi associati a oggetti specifici. Un esempio potrebbe essere il code-behind di un oggetto selezionato che viene eseguito quando tale oggetto viene attivato.

 Nella tabella seguente sono elencate le interfacce principali utilizzate dalla finestra **Proprietà.**

|Interface Name (Nome interfaccia)|Descrizione|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornisce un elenco di categorie per il **proprietà** finestra ed esegue il mapping di ogni proprietà a una categoria.|
|[Interfaccia IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Espone i metodi e le proprietà di un oggetto agli strumenti di programmazione e ad altre applicazioni che supportano l'automazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornisce i pulsanti con i *lipsia (...) denominati generatori* che aprono finestre di dialogo modali implementate dall'oggetto stesso. Utilizzato quando un valore non viene digitato facilmente dall'utente in un campo di testo. Ad esempio, potrebbe essere utilizzato per aprire un selettore colore che determina il valore RGB per l'utente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornisce l'accesso agli oggetti utilizzati per aggiornare le informazioni visualizzate nella finestra **Proprietà.** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>viene implementato da VSPackage per ogni finestra che contiene oggetti selezionabili con proprietà correlate da visualizzare.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornisce informazioni sul tipo di un oggetto, ad esempio i metodi di un'interfaccia e i campi di una struttura.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Consente ai package VS di ricevere la notifica degli eventi di selezione e di recuperare informazioni sulla gerarchia del progetto corrente, sull'elemento, sul valore dell'elemento e sul contesto dell'interfaccia utente del comando.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornisce l'ambiente con accesso a più selezioni.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilizzato per fornire nomi localizzati su alcune proprietà visualizzate nella finestra **Proprietà.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifies ai pacchetti VSPackage registrati le modifiche alla selezione, al valore dell'elemento o al contesto dell'interfaccia utente comandi correnti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica all'ambiente una modifica nella selezione corrente e fornisce l'accesso alle informazioni sulla gerarchia e sugli elementi relativi alla nuova selezione.|

 Per ulteriori `IDispatch`informazioni su , consultare MSDN Library.

## <a name="see-also"></a>Vedere anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
- [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)
