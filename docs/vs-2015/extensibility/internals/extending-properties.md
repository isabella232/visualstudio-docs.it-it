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
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690987"
---
# <a name="extending-properties"></a>Estensione delle proprietà
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] finestra **Proprietà** è un visualizzatore di proprietà universale per i componenti com e com+ e supporta tutti i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prodotti. La finestra **Proprietà** funziona con le `ITypeInfo` informazioni sul tipo e i metadati com+ per elencare le proprietà della fase di progettazione per l'oggetto attualmente selezionato in qualsiasi altra finestra del Integrated Development Environment (IDE).  
  
 La finestra **Proprietà** , che può essere aperta premendo F4 sulla tastiera oppure scegliendo **finestra Proprietà** dal menu **Visualizza** , viene utilizzata per visualizzare e modificare le proprietà e gli eventi della fase di progettazione indipendenti dalla configurazione degli oggetti selezionati. Le proprietà dipendenti dalla configurazione, associate a soluzioni e progetti, vengono visualizzate nelle [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per altre informazioni, vedere la pagina relativa alle [proprietà del progetto](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), alla gestione delle [Opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)e [alla gestione degli elementi nei progetti](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Panoramica della finestra Proprietà](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Finestra Proprietà  
  
 In questa sezione vengono fornite informazioni dettagliate relative alle singole aree della finestra **Proprietà** e alle interfacce che è necessario implementare e chiamare per popolare la finestra.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Panoramica della finestra Proprietà](../../extensibility/internals/properties-window-overview.md)  
 Viene illustrato lo scopo della finestra **Proprietà** rispetto alla finestra degli strumenti e alla finestra del documento.  
  
 [Criteri dei modelli e finestra Proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Viene illustrato il modo in cui un progetto è contenuto in un progetto modello Enterprise e il modo in cui il progetto modello Enterprise può applicare i criteri.  
  
 [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Viene illustrata la base per la selezione che determina quali informazioni vengono visualizzate nella finestra **Proprietà** .  
  
 [Elenco di oggetti della finestra Proprietà](../../extensibility/internals/properties-window-object-list.md)  
 Descrive lo scopo dell'elenco di oggetti della finestra **Proprietà** , che descrive come, quando un oggetto diverso da questo elenco attiva una chiamata, l'ambiente viene informato che è stato selezionato un nuovo oggetto.  
  
 [Pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md)  
 Viene illustrato lo scopo dei quattro pulsanti predefiniti visualizzati sulla barra degli strumenti della finestra **Proprietà** .  
  
 [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)  
 Viene illustrato dove vengono trovati i campi dei nomi di proprietà e dei valori delle proprietà nella griglia.  
  
 [Specifica della traccia della selezione per la finestra Proprietà](../../misc/announcing-property-window-selection-tracking.md)  
 Descrive il rilevamento della selezione per la finestra **Proprietà** .  
  
 [Nascondere le proprietà con proprietà figlio](../../misc/hiding-properties-that-have-child-properties.md)  
 Viene illustrato come nascondere le proprietà che dispongono di proprietà figlio implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> interfaccia.  
  
 [Specifica di una finestra Proprietà personalizzate](../../misc/providing-a-custom-properties-window.md)  
 Descrive i passaggi per fornire il proprio visualizzatore di proprietà.  
  
 [Descrizioni dei campi dalla finestra Proprietà](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Viene illustrato dove trovare l'area della descrizione che visualizza le informazioni correlate al campo della proprietà selezionata.  
  
 [Aggiornamento dei valori della proprietà nella finestra Proprietà](../../misc/updating-property-values-in-the-properties-window.md)  
 Vengono fornite istruzioni dettagliate in cui vengono illustrati i due modi per sincronizzare la finestra **Proprietà** con le modifiche al valore della proprietà.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)  
 Vengono illustrati i progetti come blocchi predefiniti dell' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Compilazione e creazione](../../ide/compiling-and-building-in-visual-studio.md)  
 Viene descritto come utilizzare la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] piattaforma per eseguire continuamente test e debug delle applicazioni durante la compilazione.  
  
 [Proprietà documento HTML, finestra Proprietà](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Vengono fornite istruzioni per la modifica di un documento HTML direttamente dalla Finestra Proprietà e viene fornita una tabella in cui vengono descritti in dettaglio i campi di un documento HTML nell'Finestra Proprietà.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Descrive l' `IDispatch` interfaccia, che è stata progettata per supportare l'automazione, fornendo un meccanismo ad associazione tardiva per accedere e recuperare informazioni sui metodi e sulle proprietà di un oggetto.  
  
 [PENNINI: Introduzione a proprietà dinamiche (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Viene fornita una panoramica delle proprietà dinamiche che consentono di configurare l'applicazione in modo che i valori delle proprietà vengano archiviati in un file di configurazione esterno anziché nel codice compilato dell'applicazione.  
  
 [NIB: Progetti come contenitori](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Descrive il ruolo del progetto come contenitore in una soluzione per gestire, compilare ed eseguire il debug in modo logico degli elementi che costituiscono l'applicazione.  
  
 [PENNINI: Proprietà progetto](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Viene descritto il modo in cui il progetto gestisce le impostazioni che consentono di controllare le proprietà che si applicano all'intero progetto e anche le proprietà limitate a determinate configurazioni di compilazione del progetto.  
  
 [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)  
 Viene illustrato come [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestire in modo efficiente gli elementi, ad esempio i riferimenti, le connessioni dati, le cartelle e i file necessari per il lavoro di sviluppo tramite soluzioni e progetti.  
  
 [Estensione di altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Spiega come usare i servizi di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].
