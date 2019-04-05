---
title: Estensione delle proprietà | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59afc6a95e327460602ece8db58f075b483d0e09
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966440"
---
# <a name="extending-properties"></a>Estensione delle proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **delle proprietà** finestra è un visualizzatore proprietà universale per i componenti COM e COM+ e supporta tutte [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prodotti. Il **delle proprietà** finestra funziona con `ITypeInfo` digitare le informazioni e i metadati di COM+ per elencare le proprietà in fase di progettazione per l'oggetto attualmente selezionato in un'altra finestra nell'ambiente di sviluppo integrato (IDE).  
  
 Il **delle proprietà** finestra, che può essere aperta, premere F4 sulla tastiera, oppure selezionando **finestra delle proprietà** sul **visualizzazione** menu, viene utilizzato per visualizzare e modificare proprietà indipendenti dalla configurazione, in fase di progettazione e gli eventi degli oggetti selezionati. Proprietà dipendenti dalla configurazione, associate a soluzioni e progetti, vengono visualizzate nella [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per altre informazioni, vedere [le proprietà del progetto: NIB](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md), e [NIB: gestione degli elementi nei progetti](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Panoramica della finestra proprietà](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Finestra Proprietà  
  
 In questa sezione vengono fornite informazioni dettagliate correlate a singole aree del **proprietà** finestra e le interfacce da implementare e chiamare per popolare la finestra.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica della finestra Proprietà](../../extensibility/internals/properties-window-overview.md)  
 Viene illustrato lo scopo del **proprietà** finestra rispetto alla finestra degli strumenti e la finestra del documento.  
  
 [Criteri dei modelli e finestra Proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Illustra come un progetto è contenuto in un progetto di modello dell'organizzazione e come tale progetto di modello aziendale può applicare i criteri.  
  
 [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Illustra la base per la selezione che determina quali informazioni vengono visualizzate nel **proprietà** finestra.  
  
 [Elenco di oggetti della finestra Proprietà](../../extensibility/internals/properties-window-object-list.md)  
 Viene descritto lo scopo del **proprietà** elenco di oggetti finestra, che descrivono come, quando un oggetto diverso da questo elenco viene attivata una chiamata, l'ambiente è stato informato che sia stato selezionato un nuovo oggetto.  
  
 [Pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md)  
 Viene illustrato lo scopo dei pulsanti quattro predefiniti visualizzati nei **proprietà** degli strumenti della finestra.  
  
 [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)  
 Viene spiegato in cui vengono trovati i nomi di proprietà e campi di valori di proprietà nella griglia.  
  
 [Specifica della traccia della selezione per la finestra Proprietà](../../misc/announcing-property-window-selection-tracking.md)  
 Viene descritto il rilevamento di selezione il **proprietà** finestra.  
  
 [Nascondere le proprietà con proprietà figlio](../../misc/hiding-properties-that-have-child-properties.md)  
 Viene spiegato come nascondere le proprietà con proprietà figlio tramite l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interfaccia.  
  
 [Specifica di una finestra Proprietà personalizzate](../../misc/providing-a-custom-properties-window.md)  
 Illustra in dettaglio la procedura per fornire il proprio browser di proprietà.  
  
 [Descrizioni dei campi dalla finestra Proprietà](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Descrive dove trovare l'area di descrizione che visualizza le informazioni relative al campo della proprietà selezionata.  
  
 [Aggiornamento dei valori della proprietà nella finestra Proprietà](../../misc/updating-property-values-in-the-properties-window.md)  
 Vengono fornite istruzioni dettagliate che illustrano due modi per mantenere la **proprietà** finestra sincronizzato con valore di proprietà cambia.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono illustrati i progetti come i blocchi predefiniti del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)  
 Descrive come è possibile usare il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] piattaforma per il test e debug delle applicazioni durante la compilazione.  
  
 [Proprietà documento HTML, finestra proprietà](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Vengono fornite istruzioni per la modifica di un documento HTML direttamente dalla finestra delle proprietà e viene fornita una tabella che riporta in dettaglio i campi in un documento HTML nella finestra Proprietà.  
  
 [IDispatch](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Viene descritto il `IDispatch` interfaccia, prima di tutto è stato progettato per supportare l'automazione, che fornisce un meccanismo di associazione tardiva per accedere e recuperare informazioni sui metodi e proprietà di un oggetto.  
  
 [NIB: Introduzione alle proprietà dinamiche (Visual Studio)](http://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fornisce una panoramica delle proprietà dinamiche che consentono di configurare l'applicazione in modo che i valori delle proprietà sono archiviati in un file di configurazione esterno anziché il codice dell'applicazione compilata.  
  
 [NIB: progetti come contenitori](http://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Descrive il ruolo del progetto come un contenitore in una soluzione per gestire in modo logico, compilazione e debug gli elementi che costituiscono l'applicazione.  
  
 [Proprietà NIB: progetto](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Viene descritto come il progetto gestisce le impostazioni che consentono di proprietà di controllo che si applicano all'intero progetto e anche le proprietà sono limitate a determinate configurazioni di compilazione del progetto.  
  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)  
 Viene spiegato come [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestisce in modo efficiente gli elementi, ad esempio i riferimenti, le connessioni dati, cartelle e file necessari per l'attività di sviluppo tramite soluzioni e progetti.  
  
 [Estensione di altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Spiega come usare i servizi di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
